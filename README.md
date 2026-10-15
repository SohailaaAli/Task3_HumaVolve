# Products API - Clean Architecture + CQRS

## المتطلبات المنفذة

1. **Product Entity** يحتوي على: `Id`, `Name`, `Price`
2. **Endpoints**:
   - `GET /api/products`
   - `GET /api/products/{id}`
   - `POST /api/products`
3. **فصل الطبقات**:
   - `Products.Domain` → Entities
   - `Products.Application` → Commands, Queries, DTOs, Validators, Interfaces
   - `Products.Infrastructure` → EF Core, SQL Server, Repositories
   - `Products.API` → Controllers
4. **EF Core + SQL Server**
5. **DTOs + FluentValidation**

## الهيكل

```
Products/
├── src/
│   ├── Products.API/
│   ├── Products.Application/
│   ├── Products.Domain/
│   └── Products.Infrastructure/
└── Products.sln
```

## كيفية التشغيل

1. تأكد من تثبيت .NET 8 SDK
2. عدّل Connection String في `appsettings.json` حسب إعدادات SQL Server عندك
3. من مجلد الحل:

```bash
dotnet restore
dotnet run --project src/Products.API
```

4. افتح Swagger على: `https://localhost:7001/swagger`

## أمثلة على الطلبات

### إنشاء منتج (POST)
```json
POST /api/products
{
  "name": "Laptop",
  "price": 15000
}
```

### جلب كل المنتجات
```
GET /api/products
```

### جلب منتج بالمعرف
```
GET /api/products/{guid}
```

## التقنيات المستخدمة

- .NET 8
- MediatR (CQRS)
- FluentValidation
- Entity Framework Core 8
- SQL Server
- Swagger
