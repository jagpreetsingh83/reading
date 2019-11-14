### Learning

1. Create more modules.
2. Create more services, 
  - a Fasade service to deal with Store. There should not be any DI of store other than fasade services. This service should also hold easy to reuse references to the store selectors on the top of the file.
  - an API service to make calls to the backend
  - a business logic service if make sense and makes your components cleaner
3. Have a meaningful store. Keep the store in their respective modules and hook them up to the root store.
4. Use maxAge, logOnly options on the redux dev tools
5. Always cleanup the selectors to release the memory
6. Using chrome profiler to identify memory leaks
7. Make sure you never have a memory leak using take, takeUntil operators
8. Use a nice logger

 
