---
title: Ajout et vérification du SIRET
level: 2
layout: section
---
# Ajout et vérification du SIRET


---
hideInToc: true
---

composer.json
```json
"ibericode/vat-bundle": "^2.0",
```

config/api_platform/customer.yaml
```yaml
App\Entity\Customer\Customer:
    collectionOperations:
        shop_post:
            input: App\Command\Account\RegisterShopUser
```

src/Command/Account/RegisterShopUser.php
```php
class RegisterShopUser extends Sylius\Bundle\ApiBundle\Command\Account\RegisterShopUser
{
    public function __construct(
        string $firstName, string $lastName, string $email, string $password,
        #[Groups('shop:customer:create')]
        public ?string $vatNumber = null
    ) {
        parent::__construct($firstName, $lastName, $email, $password, $subscribedToNewsletter);
    }
}
```

---
hideInToc: true
---

src/CommandHandler/Account/RegisterShopUserHandler.php
```php
use App\Command\Account\RegisterShopUser;
use Ibericode\Vat\Exception;

class RegisterShopUserHandler implements MessageHandlerInterface
{    
    public function __invoke(RegisterShopUser $command): ShopUserInterface 
    {
        // ...
        if ($command->vatNumber !== null) {
            if ($this->vatValidator->validateVatNumberFormat($command->vatNumber) === false) {
                throw new Exception(sprintf('VAT number format "%s" is invalid.', $command->vatNumber));
            }
            if ($this->vatValidator->validateVatNumber($command->vatNumber) === false) {
                throw new Exception(sprintf('VAT number "%s" is invalid.', $command->vatNumber));
            }
            $customer->setVatNumber($command->vatNumber);
        } else {
            throw new InvalidArgumentException('VAT number is empty.');
        }
        // ...
    }
}
```

---
hideInToc: true
---

Ne pas oublier de renvoyer la donnée dans l'API :)

src/Entity/Customer/Customer.php
```php
use Sylius\Component\Core\Model\Customer as BaseCustomer;

#[ORM\Entity]
#[ORM\Table(name: 'sylius_customer')]
class Customer extends BaseCustomer
{
    #[Groups('sylius:customer:read')]
    private $vatNumber;
}
```
