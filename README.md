### About Me

```typescript
interface Address {
  street: string;
  city: string;
}

interface Person {
  name: string;
  birth: string;
  address: Address;
}

class MyDetail<Type extends Person> {
  constructor(public myDetail: Type) {}
}

const myDetail = new MyDetail<Person>({
  name: "Ahmad Beni Rusli",
  birth: "Cilacap, 23 July 2005",
  address: {
    street: "Jln. Cipari no 4",
    city: "Cilacap"
  }
});
```

<p align="center" style="width: 100%;"><a href="https://github.com/Abrazax56"><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Abrazax56&theme=dark&layout=compact"></a></p>
