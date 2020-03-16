## pnpm prune bug reproduction

1. Install all dependencies
    ```
    pnpm recursive install
    ```

2. Check `node_modules` size
    ```
    du -sh node_modules # 27M
    ```

3. Prune devDeps
    ```
    pnpm recursive prune --prod
    ```

4. Check `node_modules` size
    ```
    du -sh node_modules # Still 27M!
    ```

5. Clean up node_modules manually
    ```
    rm -rf ./node_modules
    rm -rf ./packages/*/node_modules
    ```

6. Install without devDeps
    ```
    NODE_ENV=production pnpm recursive install
    ```

7. Check `node_modules` size
    ```
    du -sh node_modules # 488K!
    ```
