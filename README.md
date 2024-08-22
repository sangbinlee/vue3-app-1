# vue3-app-1

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

"# vue3-app-1"

    C:\Users\sangb\vue3>npm create vue@latest
    Need to install the following packages:
    create-vue@3.10.4
    Ok to proceed? (y)


    > npx
    > create-vue


    Vue.js - The Progressive JavaScript Framework

    √ Project name: ... vue3-app-1
    √ Add TypeScript? ... No / Yes
    √ Add JSX Support? ... No / Yes
    √ Add Vue Router for Single Page Application development? ... No / Yes
    √ Add Pinia for state management? ... No / Yes
    √ Add Vitest for Unit Testing? ... No / Yes
    √ Add an End-to-End Testing Solution? » No
    √ Add ESLint for code quality? ... No / Yes
    √ Add Prettier for code formatting? ... No / Yes
    √ Add Vue DevTools 7 extension for debugging? (experimental) ... No / Yes

    Scaffolding project in C:\Users\sangb\vue3\vue3-app-1...

    Done. Now run:

    cd vue3-app-1
    npm install
    npm run dev


    C:\Users\sangb\vue3>npm create vue@latest

    C:\Users\sangb\vue3>  cd vue3-app-1

    C:\Users\sangb\vue3\vue3-app-1>  npm install
    npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
    npm warn deprecated @humanwhocodes/config-array@0.11.14: Use @eslint/config-array instead
    npm warn deprecated rimraf@3.0.2: Rimraf versions prior to v4 are no longer supported
    npm warn deprecated glob@7.2.3: Glob versions prior to v9 are no longer supported
    npm warn deprecated @humanwhocodes/object-schema@2.0.3: Use @eslint/object-schema instead

    added 136 packages, and audited 137 packages in 18s

    29 packages are looking for funding
    run `npm fund` for details

    found 0 vulnerabilities

    C:\Users\sangb\vue3\vue3-app-1>  npm run dev

    > vue3-app-1@0.0.0 dev
    > vite


    VITE v5.3.4  ready in 1606 ms

    ➜  Local:   http://localhost:5173/
    ➜  Network: use --host to expose
    ➜  press h + enter to show help

# preview - 운영서버

    server {
        server_name vite.sodi9.store;
        root /var/www/vite;
        index index.html;

        # location / {
        #        try_files $uri $uri/ =404;
        #}

        listen [::]:443 ssl ipv6only=on; # managed by Certbot
        listen 443 ssl; # managed by Certbot
        ssl_certificate /etc/letsencrypt/live/vite.sodi9.store/fullchain.pem; # managed by Certbot
        ssl_certificate_key /etc/letsencrypt/live/vite.sodi9.store/privkey.pem; # managed by Certbot
        include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
        ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

        location / {

                proxy_set_header        Host $host;
                proxy_set_header        X-Real-IP $remote_addr;
                proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header        X-Forwarded-Proto $scheme;

                # Fix the "It appears that your reverse proxy set up is broken" error.
                proxy_pass          http://127.0.0.1:3004;
                proxy_read_timeout  90;
        }
    }

    server {
            if ($host = vite.sodi9.store) {
                    return 301 https://$host$request_uri;
            } # managed by Certbot


            listen 80;
            listen [::]:80;
            server_name vite.sodi9.store;
            return 301 https://$host$request_uri;

    }

# dist 위치를 nginx root로 만드는 방식 - 개발서버 테스트용.

    # vue3 block to proxy requests to Jenkins running on port 8081

    server {
        if ($host = vue3.sodi9.store) {
                    return 301 https://$host$request_uri;
        } # managed by Certbot

        listen 80;
        server_name vue3.sodi9.store;
        return 404;
    }

    server {
        root /var/lib/jenkins/workspace/vue3/dist;
        #root /var/www/vue3;
        index index.html;
        listen 443 ssl http2;
        listen [::]:443 ssl http2;
        server_name vue3.sodi9.store;
        ssl_certificate /etc/letsencrypt/live/vue3.sodi9.store/fullchain.pem; # managed by Certbot
        ssl_certificate_key /etc/letsencrypt/live/vue3.sodi9.store/privkey.pem; # managed by Certbot
        include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
        ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
    }

# port 정보

    default
    sodi9.store
    8080 jenkins.sodi9.store
    3000 nuxt.sodi9.store
    3001 dashboard.sodi9.store
    3002 sales.sodi9.store
    3003 next.sodi9.store
    3004 vite.sodi9.store
    3005 landing.sodi9.store
    3006 vue3.sodi9.store

# server https
