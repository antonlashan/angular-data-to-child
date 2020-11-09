# angular-data-to-child

*parent.component.html*

```html
<child
    ...
    [data]="employees"
>
</child>
```

*parent.component.ts:*

```ts
employees = [];

ngOnInit() {
    this.getEmployees();
}

getEmployees() {
    this.employeeService.get().subscribe((list: EmployeeDto) => {
      this.employees = list.items;
    });
}
```

*child.component.ts:*
```ts
  private _data = [];
  @Input() set data(d: any[]) {
    this._data = d;
    this.options = d;
  }
  get data() {
    return this._data;
  }
  @Input() options: any[] = [];
```
