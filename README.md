# Payment System Architecture

Цей проєкт реалізує архітектуру платіжної системи з використанням патернів **Factory Method** та **Abstract Factory** у TypeScript. Система підтримує обробку платежів через різні провайдери (Stripe, PayPal, ApplePay) з імітацією платіжного циклу (`authorize`, `capture`, `refund`). Архітектура спроєктована для гнучкості, масштабованості та легкого додавання нових провайдерів.

## Мета проєкту

Проєкт демонструє використання патернів проєктування для:
- Відокремлення створення об’єктів від їх використання.
- Забезпечення гнучкості та масштабованості системи.
- Ізоляції логіки створення платіжних провайдерів за допомогою фабрик.

## Структура проєкту


neo-design-patterns-hw-03/
├── src/
│   ├── core/
│   │   ├── PaymentProvider.ts
│   │   └── PaymentProviderFactory.ts
│   ├── providers/
│   │   ├── stripe/
│   │   │   ├── StripePaymentProvider.ts
│   │   │   └── StripeFactory.ts
│   │   ├── paypal/
│   │   │   ├── PaypalPaymentProvider.ts
│   │   │   └── PaypalFactory.ts
│   │   ├── apple/
│   │   │   ├── ApplePaymentProvider.ts
│   │   │   └── AppleFactory.ts
│   ├── app/
│   │   └── PaymentContext.ts
│   ├── main.ts
├── package.json
├── tsconfig.json
├── .gitignore
└── README.md


## Використані патерни

- **Factory Method**: Кожен клас фабрики (`StripeFactory`, `PaypalFactory`, `AppleFactory`) реалізує інтерфейс `PaymentProviderFactory` і відповідає за створення відповідного платіжного провайдера (`StripePaymentProvider`, `PaypalPaymentProvider`, `ApplePaymentProvider`).
- **Abstract Factory**: Інтерфейс `PaymentProviderFactory` дозволяє створювати об’єкти провайдерів абстрактно, забезпечуючи уніфікований доступ до різних платіжних систем через `PaymentContext`.

## Переваги архітектури

- **Гнучкість**: Додавання нового провайдера (наприклад, GooglePay) вимагає лише створення нового класу провайдера та фабрики без зміни основної логіки.
- **Ізоляція створення об’єктів**: Використання `new` обмежено фабриками, що спрощує заміну реалізації провайдерів.
- **Типобезпека**: Використання TypeScript забезпечує сувору типізацію та зменшує ризик помилок.
- **Модульність**: Код структуровано за модулями, що полегшує підтримку та тестування.

## Встановлення
1. Клонуйте репозиторій.
2. Виконайте `npm install` для встановлення залежностей.

## Використання
Запустіть програму з одним із провайдерів:
```bash
npx ts-node src/main.ts stripe
npx ts-node src/main.ts paypal
npx ts-node src/main.ts apple
