# 💳 Payment System Architecture

Цей проєкт реалізує архітектуру платіжної системи з використанням патернів **Factory Method** та **Abstract Factory** у TypeScript. Система підтримує обробку платежів через різні провайдери: **Stripe**, **PayPal**, **ApplePay** — з імітацією платіжного циклу (`authorize`, `capture`, `refund`).

> Архітектура спроєктована для гнучкості, масштабованості та легкого додавання нових провайдерів.

---

## 🎯 Мета проєкту

- Відокремити створення об’єктів від їх використання.
- Забезпечити гнучкість і масштабованість системи.
- Ізолювати логіку створення платіжних провайдерів за допомогою фабрик.

---

## 🧩 Структура проєкту

```
neo-design-patterns-hw-03/
├── src/
│   ├── app/
│   │   └── PaymentContext.ts
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
│   └── main.ts
├── package.json
├── tsconfig.json
├── .gitignore
└── README.md
```

---

## 🏗️ Використані патерни

- **Factory Method**  
  Кожна фабрика (`StripeFactory`, `PaypalFactory`, `AppleFactory`) реалізує інтерфейс `PaymentProviderFactory` і відповідає за створення відповідного платіжного провайдера.

- **Abstract Factory**  
  Інтерфейс `PaymentProviderFactory` дозволяє створювати об’єкти провайдерів абстрактно. Це забезпечує уніфікований доступ до платіжних систем через `PaymentContext`.

---

## ✅ Переваги архітектури

- **Гнучкість**: додавання нового провайдера (наприклад, GooglePay) вимагає лише створення нового класу провайдера та фабрики.
- **Ізоляція створення**: використання `new` зосереджене лише у фабриках.
- **Типобезпека**: використання TypeScript забезпечує сувору типізацію.
- **Модульність**: код структурований, легко підтримується й тестується.

---

## ⚙️ Встановлення

```bash
git clone https://github.com/your-username/neo-design-patterns-hw-03.git
cd neo-design-patterns-hw-03
npm install
```

---

## 🚀 Використання

Запустіть програму з потрібним провайдером:

```bash
npx ts-node src/main.ts stripe
npx ts-node src/main.ts paypal
npx ts-node src/main.ts apple
```

---

## 📂 Ліцензія

MIT License.  
© 2025 [Твоє ім’я або GitHub профіль]
