# Bounce


## Цель создания игры

В далёком прошлом я с друзьями любил играть в игру под названием "Bounce". Возможно, это была моя самая первая игра, в которой я тратил своё свободное время. Недавно я захотел отдать дань памяти этой простой и в то же время интересной игре, написав простенькую копию с первым уровнем игры из оригинала.


## Краткое описание игры

Задача игрока заключается в ведении мяча до портала. Управление осуществляется с помощью кнопок "вверх", "вниз", "вправо", "влево".


## Как установить эту игру (На Windows)

### Для начала в корне проекта следует выполнить команды

```git submodule init```

```git submodule add https://github.com/google/googletest```

Эти 2 команды создадут директорию в корне под названием googletest, где будут храниться исходники наших тестов.
Далее все стандартно: запускаем conan (подключаем библиотеку) и собираем с помощью cmake.
При клоинровании, чтобы выкачать зависимости (googletest) нужно будет выполнить команду 

```git submodule update --init --recursive```

### В cmd строке прописать следующие команды :

```conan remote add bincrafters https://api.bintray.com/conan/bincrafters/public-conan```

```conan profile new default --detect```

```conan profile update settings.cppstd=17 default```

```conan remote update bincrafters https://bincrafters.jfrog.io/artifactory/api/conan/public-conan```

```conan config set general.revisions_enabled=1```

### В корень проекта добавим папку :

```res```

### В директории, где находится проект, выполнить команды :

```conan install . -if build```

```cmake -G "Visual Studio 16 2019" -B build -S .```

```cmake --build build --config Release```

```start ./build/bin/bounce.exe```