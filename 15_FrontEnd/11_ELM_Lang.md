http://langintro.com/elm-howtos/install_ubuntu/

see script to download in:
https://github.com/elm-lang/elm-platform

```bash
mkdir npm-global
npm config set prefix /$HOME/npm-global
sudo ln -s /usr/bin/nodejs /usr/bin/node

npm i -g elm
npm i -g elm-platform-bin
```

1. sudo apt-get install haskell-platform
2. sudo apt-get install cabal-install
3. cabal update && cabal install cabal-install
4. vi .profile
add to path: $HOME/Elm-Platform/0.18/.cabal-sandbox/bin
5. runhaskell BuildFromSource.hs 0.18
6. test: elm-make --help


install elm-format:
```bash
wget -qO- https://get.haskellstack.org/ | sh
git clone https://github.com/avh4/elm-format.git

cd elm-format
stack setup
stack build
stack install
```

tutorials:
https://jazmit.github.io/2015/06/17/elm-admin-interface.html
http://courses.knowthen.com
