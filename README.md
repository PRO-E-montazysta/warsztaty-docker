# warsztaty-docker

Repozytorium ma na celu prezentację narzędzi związanych z technologią konteneryzacji w ramach przedmiotu PRO na Polsko-Japońskiej Akademii Technik Komputerowych.

Aby wziać czynny udział w warsztatach należy:
1. Pobrać repozytorium komendą:
  git clone git@github.com:PRO-E-montazysta/warsztaty-docker.git
2. Utworzyć nowy branch (najlepiej by nazwa brancha była taka sama jak twój numer indeksu) i się na niego zcheckoutować komendą: 
  git checkout -b <nazwa_brancha>
2.a. Opcjonalnie wprowadzić jakieś zmiany w aplikacji, dla chętnych można nawet podgrać coś własnego, będzie tylko trzeba zmienić ostatnią linijkę w Dockerfile. 
3. Wypushować swojego brancha do repozytorium zdalnego:
  git push <nazwa brancha> <nazwa brancha>
  
To by było na tyle, jeśli chodzi o pracę z repo.
Przechodzimy do:
https://github.com/PRO-E-montazysta/warsztaty-docker/actions
i szukamy piepline'u obsługującego nasz branch. Po czym go rozpoznać? Będzie się nazywał jak nasz branch :) 
Możemy do niego przejść i zobaczyć co w ramach takiego pipeline'u się uruchamia.

(Powyższe kroki można uzyskać wykorzystując komendy:
  docker build -t emontaztysta.pl/emontazysta/warsztaty-docoker:<tag> 
  docker login emontaztysta.pl/emontazysta/warsztaty-docoker
  docker push emontaztysta.pl/emontazysta/warsztaty-docoker:<tag>
  
Po pomyślnie zakończonym wykonaniu pipeline'a przechodzimy na:
https://warsztaty.emontazysta.pl/
Logujemy się używając credentiali, które dostaliśmy 14 stycznia na maila uczelnianego od admin@emontazysta.pl

Tutaj w menu po lewej stronie możemy przejść do Registries znajdującego się pod opcją Host, po czym wybrać Browse i sprawdzić czy nasz obraz został poprawnie załadowany do rejestru dockerowego.
  
 Następnie przechodzimy do strony Containers i wybieramy w prawym górnym rogu niebieski przycisk "+ Add container". Odpowiednio wypełniamy pola, jako nazwę proponuję znowu nr. Twojego indeksu, tak by uniknąć konfliktu z innymi uczestnikami warsztatu. Jako port mozemy wybrać albo by portainer udostępnił naszą apkę na losowych, wolnych portach, albo użyć znowu naszego numeru indeksu. Po takim skonfigurowaniu, możesz śmiało wybrać "Deploy the container". Kontener o wcześniej wybranej nazwie powinien sie pojawic wsrod uruchomionych kontenerów, możemy przejść teraz, np. do jego logów, bądź nawet wejść na sam kontener, np. w celu debugowania. Po zapoznaniu się z Twoim kontenerem uprzejmie prosze o usunięcie go, tak by nie kolidował on z kontenerami tworzonymi w dalszej części kursu.
  
  Pora przejść do kwestii docer-compose. Docker compose to narzędzie umożliwające przetrzymywanie konfiguracji uruchomieniowej kontenerów w formie kodu, jak i na uruchamianie wielu kontenerów w tzw. stackach. Aby tego dokonać przechodzimy do strony "Stacks" z menu po lewej stronie i wybieramy "+ Add stack". Wpisujemy nazwę naszego stacka, następnie w polu "Web editor" wklejamy zawartość pliku [.build/stack.yml](https://github.com/PRO-E-montazysta/warsztaty-docker/blob/7a6850ecccc09bae42f3be64b4afa14a74684e0d/.build/stack-file.yml). Modyfikujemy porty tak by ze sobą nie kolidowały, proponuje znowu nr indeksu i +1 dla każdego kolejnego konteneru w stacku. Klikamy "Deploy the stack" i tak jak w punkcie poprzednim możemy sprawdzić stan uruchomionych, tym razem w ramach naszego stacka, kontenerów.
  
  W tym miejscu część warsztatowa się kończy, a ja zapraszam Państwa do dalszej części prezentacji, w której to omówimy kwestię orkiestratorów oraz architektury środowiska aplikacji E-montazysta.
