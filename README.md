# Projekt 2
## Link do repozytorium
[https://github.com/Calslock/chmurki-2-1](https://github.com/Calslock/chmurki-2-1)
[https://hub.docker.com/repository/docker/calslock/zad2](https://hub.docker.com/repository/docker/calslock/zad2)
### Zadanie 1
[Link do zadania Github Actions](https://github.com/Calslock/chmurki-2-1/actions/runs/1732760623)
Do wykonania zadania 1 wykorzystano plik Dockerfile, przy pomocy którego budowana jest aplikacja webowa. W celu uruchomienia zadania poprzez Github Actions stworzono workflow, w którym użyto pliku [main.yml](https://github.com/Calslock/chmurki-2-1/blob/master/.github/workflows/main.yml).
### Zadanie 2
[Link do zadania Github Actions](https://github.com/Calslock/chmurki-2-1/actions/runs/1732847805)
W celu zbudowania obrazów multi-platformowych dodano do pliku [main2.yml](https://github.com/Calslock/chmurki-2-1/blob/master/.github/workflows/main2.yml) sekcję, w której zadeklarowano wykorzystanie platformy QEMU:
```
- name: Set up QEMU
  uses: docker/setup-qemu-action@master
  with:
  platforms: all
```
jak również zadeklarowano docelowe platformy w sekcji Build and Push:
`platforms: linux/amd64, linux/arm64/v8, linux/arm/v7`
### Zadanie 3
[Link do zadania Github Actions](https://github.com/Calslock/chmurki-2-1/actions/runs/1732933031)
Do wykonania zadania 3 wykorzystano plik Dockerfile.v2, w którym zadeklarowano wieloetapowe tworzenie obrazów. Dzięki uprzedniemu wykorzystaniu silnika BuildKit, nie jest konieczna żadna zmiana w pliku yml ([main3.yml](https://github.com/Calslock/chmurki-2-1/blob/master/.github/workflows/main3.yml)).
### Zadanie 4
Do wykonania zadania 4 wykorzystano wbudowaną w build-push-action funkcję cachowania. W sekcji Build and Push zadeklarowano lokalizację przechowywania cachu:
```
cache-from: type=registry,ref=calslock/zad2:image4-cache
cache-to: type=registry,ref=calslock/zad2:image4-cache,mode=max
```
Dzięki wykorzystaniu mechanizmu cachowania czas tworzenia obrazu skrócił się o ponad połowę, z 2 minut do 40 sekund.

[Zadanie GA - pierwsze uruchomienie](https://github.com/Calslock/chmurki-2-1/actions/runs/1733091649)

[Zadanie GA - ponowne uruchomienie z wykorzystaniem cache](https://github.com/Calslock/chmurki-2-1/actions/runs/1733098512)
