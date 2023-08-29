# hangyang.github.io
personal blog

## install
- install ruby first, better with [rvm](https://rvm.io/)
```bash
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```
```bash
\curl -sSL https://get.rvm.io | bash
```

```bash
rvm list
rvm install 2.6.5
```
- install [bundler](https://bundler.io/)
```bash
gem install bundler
```
- install [jekyll](https://jekyllrb.com/docs/)

```bash
gem install jekyll
```

- install dependencies
```bash
bundle install
```

## run on local 
```bash
bundle exec jekyll serve
```

## write new post

create `.md` file or `.html` file in `_post` folder

## build before push
```bash
bundle exec jekyll build
```
