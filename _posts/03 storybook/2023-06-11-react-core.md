---
title: react-core (storybook, prettier, tailwindcss) 환경 설정
Author: JUNG YoungKyun
date: 2023-06-11
category: 03 storybook
layout: post
---

아래 명령어는 core 환경 설정하려고 쳤던 명령어 입니다.
순서가 조금 이상한거 같은데, 다음에 제대로 해서 다시 올리도록 하겠습니다.

아래의 vs code 확장 프로그램도 설치 해주었습니다.

- Tailwind CSS IntelliSense
- Prettier - Code formatter

1. 스토리북 설치

    ```
    npx storybook@latest init
    ```

    1. .storybook/main.js

        ```
        /** @type { import('@storybook/react-webpack5').StorybookConfig } */
        const config = {
        stories: ['../src/**/*.mdx', '../src/**/*.stories.@(js|jsx|ts|tsx)'],
        addons: [
            '@storybook/addon-links',
            '@storybook/addon-essentials',
            '@storybook/preset-create-react-app',
            '@storybook/addon-interactions',
            {
            name: '@storybook/addon-styling',
            options: {
                // Check out https://github.com/storybookjs/addon-styling/blob/main/docs/api.md
                // For more details on this addon's options.
                postCss: true,
            },
            },
        ],
        framework: {
            name: '@storybook/react-webpack5',
            options: {},
        },
        docs: {
            autodocs: 'tag',
        },
        staticDirs: ['../public'],
        };
        export default config;
        ```
    
    2. .storybook/preview.js

        ```
        /** @type { import('@storybook/react').Preview } */
        import '../src/index.css'; // replace with the name of your tailwind css file

        const preview = {
        parameters: {
            actions: { argTypesRegex: '^on[A-Z].*' },
            controls: {
            matchers: {
                color: /(background|color)$/i,
                date: /Date$/,
            },
            },
        },
        };

        export default preview;
        ```

2. prettier 및 prettier-plugin-tailwindcss 설치

    ```
    npm install -D prettier prettier-plugin-tailwindcss
    ```

3. prettier 설치

    ```
    npm install --save-dev prettier
    ```

    1. .prettierrc.js

        ```
        module.exports = {
            singleQuote: true,
            trailingComma: 'all',
            printWidth: 100,
        };
        ```

    2. prettier.config.js

        ```
        module.exports = {
            plugins: [require('prettier-plugin-tailwindcss')],
            tailwindConfig: './styles/tailwind.config.js',
        };
        ```
    
4. storybook cli 설치

    ```
    npx @storybook/cli sb init
    ```

5. sb 업그레이드

    ```
    npx sb@latest upgrade
    ```

6. postcss 설치 같음

    ```
    npm i -D @storybook/addon-styling postcss autoprefixer
    ```

    1. postcss.config.js

        ```
        module.exports = {
            plugins: {
                tailwindcss: {},
                autoprefixer: {},
            },
        };
        ```

7. tailwindcss 설치

    ```
    npm install -D tailwindcss
    npx tailwindcss init
    ```

    1. src/index.css

        ```
        @tailwind base;
        @tailwind components;
        @tailwind utilities;

        body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
            'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
            sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        }

        code {
        font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
            monospace;
        }
        ```
        
    2. tailwind.config.js

        ```
        /** @type {import('tailwindcss').Config} */
        module.exports = {
            content: [
                "./src/**/*.{js,jsx,ts,tsx}",
            ],
            theme: {
                extend: {},
            },
            plugins: [],
        }
        ```

8. next 설치

    ```
    npx create-next-app next-storybook
    ```

9. tailwindcss 설치

    ```
    npx tailwindcss init -p
    ```
