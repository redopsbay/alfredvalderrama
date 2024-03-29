# My Hugo Site 😎

[https://redopsbay.dev](https://redopsbay.dev)

# Hugo Development 🚧 ##


### Creating the site 
```bash
docker run --rm -it \
    -v "$(pwd)":/src \
    klakegg/hugo:0.111.3-ext-ubuntu new site hugo
```

### Downloading the theme
```bash
cd hugo/
git submodule add https://github.com/kaapiandcode/hugo-goa themes/hugo-goa 
```


### Starting hugo server
```bash
docker run --rm -it \
    -v $(pwd):/src \
    -p 1313:1313 \
    klakegg/hugo:0.111.3-ext-ubuntu \
  server --disableFastRender
```


### Compiling the hugo site
```bash
docker run --rm -it \
    -v $(pwd)/hugo:/src \
    klakegg/hugo:0.111.3-ext-ubuntu \
    --gc \
    --minify \
    --baseURL "https://redopsbay.dev"
```

### Running the static site
```bash
pushd docs/
docker run --rm \
    -it \
    -p 8080:80 \
    --name nginx-server \
    -v $(pwd):/usr/share/nginx/html nginx:alpine
popd
```