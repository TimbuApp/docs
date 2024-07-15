---
sidebar_position: 1
---

# Timbu API with Next.js

Learn how to integrate **Timbu Api** with **Next.js** using axios.

## Understanding Timbu API

Before we start coding, let's understand the basic endpoints we'll use:

- **Get All Products:** 
```bash
https://api.timbu.cloud/products?organization_id=your-org-id&reverse_sort=false&page=1&size=10&Appid=your-app-id&Apikey=your-api-key
```
- **Get a Single Product:** 
```bash
https://api.timbu.cloud/products/your-product-id?organization_id=your-org-id&Appid=your-app-id&Apikey=your-api-key
```

## Folder Structure

```bash
-📁app
    -📁api
        -📁product
            -📁[productId]
                -📄route.ts
            -📄route.ts
```

## Setting Up Route Handlers

In your product **route.ts**, import axios and set up a GET function:

```typescript
import axios from "axios";
import { NextResponse } from "next/server";

export async function GET(req: Request) {
  try {
    const response = await axios.get(
      "https://api.timbu.cloud/products?organization_id=your-org-id&reverse_sort=false&page=1&size=10&Appid=your-app-id&Apikey=your-api-key"
    );

    return NextResponse.json(response.data);
  } catch (error) {
    console.log("[PRODUCT_GET]", error);
    return new NextResponse("Internal error");
  }
}
```

## Displaying Products

```typescript
  const [products, setProducts] = useState<Products | null>(null);

  useEffect(() => {
    axios.get("/api/products").then((response) => {
      setProducts(response.data);
    });
  }, []);
```

In your **typings.d.ts** file:

```typescript
interface Category {
    organization_id: string;
    name: string;
    position: number | null;
    category_type: string;
    description: string;
    last_updated: string;
    id: string;
    parent_id: string | null;
    url_slug: string | null;
    is_deleted: boolean;
    date_created: string;
    subcategories: any[];
    parents: any[];
  }
  
  interface Photo {
    model_name: string;
    model_id: string;
    organization_id: string;
    filename: string;
    url: string;
    is_featured: boolean;
    save_as_jpg: boolean;
    is_public: boolean;
    file_rename: boolean;
    position: number;
  }
  
  interface Price {
    NGN: [number, null, any[]];
  }
  
  interface Item {
    name: string;
    description: string;
    unique_id: string;
    url_slug: string;
    is_available: boolean;
    is_service: boolean;
    previous_url_slugs: string | null;
    unavailable: boolean;
    unavailable_start: string | null;
    unavailable_end: string | null;
    id: string;
    parent_product_id: string | null;
    parent: string | null;
    organization_id: string;
    product_image: any[];
    categories: Category[];
    date_created: string;
    last_updated: string;
    user_id: string;
    photos: Photo[];
    current_price: Price[];
    is_deleted: boolean;
    available_quantity: number;
    selling_price: number | null;
    discounted_price: number | null;
    buying_price: number | null;
    extra_infos: any;
  }
  
  interface Products {
    page: number;
    size: number;
    total: number;
    debug: any | null;
    previous_page: any | null;
    next_page: any | null;
    items: Item[];
  }
```