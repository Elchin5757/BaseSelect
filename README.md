# O'zbekcha documentatsiya Pastroqda
# baseselect

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
    1) Run `Extensions: Show Built-in Extensions` from VSCode's command palette
    2) Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
yarn
```

### Compile and Hot-Reload for Development

```sh
yarn dev
```

### Type-Check, Compile and Minify for Production

```sh
yarn build
```

# Base selectning ishlatilishi
Bu Base Select headlessui yordamida yasalgan [headlessui](https://headlessui.com/)

1. Bu componentni ishlatish uchun proektingizda [tailwindcss](https://tailwindcss.com/) va [headlessui](https://headlessui.com/) kutibhonalari bolishi kerak  
2. src folder ichida components folderi bor uning ichida esa BaseSelect degan vue file bor shu Selectning kodlari uni olib oz componentlaringizga qo'shing
3. Selectni sizga kerakli file ga import qiling
4. Selectning v-model directiviga o'z o'zgaruvchingizni bog'lang
5. Selectda dropdownida chiqishi kerak bo'lgan (productlarni) ulang 
6. Selctga placeholder, label va class qo'shishingiz mumkin 
7. Selectga hatolikni korsatish uchun error-message directiveida foydalanging
