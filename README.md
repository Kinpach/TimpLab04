export GITHUB_USERNAME=Kinpach
export GITHUB_TOKEN=***
cd ${GITHUB_USERNAME}/workspace
source scripts/activate
git clone https://github.com/${GITHUB_USERNAME}/TimpLab03 projects/TimpLab04
Клонирование в «projects/TimpLab04»...
remote: Enumerating objects: 56, done.
remote: Counting objects: 100% (56/56), done.
remote: Compressing objects: 100% (29/29), done.
remote: Total 56 (delta 19), reused 52 (delta 18), pack-reused 0 (from 0)
Получение объектов: 100% (56/56), 15.59 КиБ | 149.00 КиБ/с, готово.
Определение изменений: 100% (19/19), готово.
cd projects/TimpLab04
git remote remove origin
git remote add origin https://github.com/${GITHUB_USERNAME}/TimpLab04
cat > .travis.yml <<EOF
language: cpp
EOF
cat >> .travis.yml <<EOF
script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
cat >> .travis.yml <<EOF
addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
git add .travis.yml
git add README.md
git commit -m"added CI"
[master 3230758] added CI
 2 files changed, 13 insertions(+)
 create mode 100644 .travis.yml
git push origin master
Username for 'https://github.com': Kinpach
Password for 'https://Kinpach@github.com': 
Перечисление объектов: 60, готово.
Подсчет объектов: 100% (60/60), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (32/32), готово.
Запись объектов: 100% (60/60), 16.04 КиБ | 8.02 МиБ/с, готово.
Всего 60 (изменений 21), повторно использовано 54 (изменений 19), повторно использовано пакетов 0
remote: Resolving deltas: 100% (21/21), done.
To https://github.com/Kinpach/TimpLab04
 * [new branch]      master -> master
