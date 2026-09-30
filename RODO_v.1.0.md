# README: LOGIKA I ZAŁOŻENIA PROJEKTU

## 1. Cel projektu

Projekt został zbudowany jako lekki system zarządzania zgodnością z RODO dla małej, w szczególności jednoosobowej, praktyki lekarskiej.

Jego celem nie jest stworzenie możliwie dużej liczby dokumentów ani odwzorowanie rozbudowanego systemu compliance właściwego dla dużej organizacji. Celem jest utrzymywanie **spójnego modelu rzeczywistego przetwarzania danych**, na podstawie którego można wykazać:

* jakie dane są przetwarzane i w jakim celu,
* na jakiej podstawie odbywa się przetwarzanie,
* jakie osoby, systemy i podmioty uczestniczą w przetwarzaniu,
* jakie ryzyka z niego wynikają,
* jakie zabezpieczenia zastosowano,
* jakie obowiązki organizacyjne z tego wynikają,
* jakie zdarzenia faktycznie miały miejsce,
* czy system pozostaje aktualny i adekwatny.

Podstawowym założeniem jest więc:

**dokumentacja ma być reprezentacją funkcjonującego systemu ochrony danych, a nie niezależnym zbiorem dokumentów tworzonych wyłącznie w celu wykazania zgodności.**

---

# 2. Ogólna architektura logiczna

Projekt można rozumieć jako kilka powiązanych warstw:

**rzeczywiste przetwarzanie → opis procesów → wymagania → ryzyko → zabezpieczenia → dokumentacja → eksploatacja i zdarzenia → przegląd**

Warstwy te nie są niezależnymi modułami.

Procesy przetwarzania określają, co rzeczywiście dzieje się z danymi. Na tej podstawie powstaje Rejestr Czynności Przetwarzania (RCP) i identyfikowane są wymagania. Charakter przetwarzania i wykorzystywanych zasobów pozwala następnie ocenić ryzyko. Ryzyko wpływa na dobór zabezpieczeń. Zabezpieczenia i sposób działania organizacji są formalizowane przez polityki i procedury. Rejestry dokumentują natomiast konkretne zdarzenia zachodzące podczas funkcjonowania systemu.

Model tworzy dzięki temu zamknięty cykl:

**identyfikacja → ocena → zabezpieczenie → działanie → rejestracja → kontrola → aktualizacja.**

---

# 3. Czynność przetwarzania jako punkt wyjścia

Podstawowym obiektem biznesowym nie jest dokument, system informatyczny ani pojedyncza operacja na danych, lecz **czynność/proces przetwarzania realizowany w określonym celu**.

Przykładami takich czynności / procesów są m.in.:

* rejestracja i obsługa wizyt,
* udzielanie świadczeń i prowadzenie dokumentacji medycznej,
* udostępnianie dokumentacji,
* rozliczenia,
* obsługa korespondencji,
* realizacja obowiązków prawnych.

Proces nie powinien być rozbijany na każdą techniczną operację. Logowanie do systemu, zapis rekordu, wykonanie wydruku czy wysłanie informacji nie muszą automatycznie stawać się osobnymi czynnościami przetwarzania.

Jednocześnie proces nie powinien być tak szeroki, aby tracił znaczenie analityczne.

Przyjęty poziom szczegółowości ma odpowiadać przede wszystkim **celowi i kontekstowi przetwarzania**, a nie architekturze technicznej.

Ewidencja typów tych czynności / procesów przechowywana jest w Rejestrze Czynności Przetwarzania (RCP).
---

# 4. RCP jako mapa przetwarzania

RCP nie jest traktowany jako odizolowany dokument wymagany przez RODO.

W modelu pełni funkcję **centralnej mapy działalności związanej z danymi osobowymi**.

Łączy proces z jego podstawowymi właściwościami, takimi jak:

**cel → osoby → dane → podstawa prawna → odbiorcy → procesorzy/systemy → retencja → zabezpieczenia.**

Dzięki temu RCP jest punktem odniesienia dla pozostałych elementów systemu.

Nie oznacza to jednak, że wszystkie informacje muszą być fizycznie zapisane bezpośrednio w RCP. Projekt świadomie rozdziela informacje na osobne słowniki i rejestry, jeżeli mają własny cykl życia lub są wykorzystywane w wielu miejscach.

RCP jest zatem przede wszystkim **warstwą relacyjną**, która wiąże informacje istniejące w modelu.

---

# 5. Słowniki jako wspólny język systemu

Powtarzalne pojęcia są w miarę możliwości definiowane raz i później wykorzystywane przez pozostałe elementy modelu.

Dotyczy to szczególnie:

* procesów,
* kategorii danych,
* kategorii osób,
* odbiorców,
* systemów,
* procesorów,
* zabezpieczeń,
* typów zdarzeń,
* klasyfikacji ryzyka.

Słownik nie służy wyłącznie wygodzie technicznej. Jego podstawową funkcją jest zapewnienie **jednolitego znaczenia pojęć w całym projekcie**.

Jeżeli np. określone zabezpieczenie występuje przy wielu ryzykach, powinno zachowywać tę samą tożsamość i znaczenie.

---

# 6. Logika modelu ryzyka

Analiza ryzyka została oddzielona od RCP, ponieważ są to dwa różne spojrzenia na system.

RCP odpowiada przede wszystkim na pytanie:

**„co i dlaczego przetwarzamy?”**

Analiza ryzyka odpowiada natomiast:

**„co może się wydarzyć i jakie mogą być tego konsekwencje?”**

Ryzyko nie jest utożsamiane ani z samym zagrożeniem, ani z podatnością.

Model rozdziela logicznie:

**obszar/zasób → przyczynę → zdarzenie → naruszoną właściwość informacji → skutek → ryzyko.**

Dzięki temu podobne scenariusze mogą być analizowane w różnych częściach systemu bez tworzenia całkowicie nowych opisów.

---

# 7. Poufność, integralność i dostępność

Skutki zdarzeń analizowane są z perspektywy podstawowych właściwości informacji:

* **poufności** – dane trafiają do osoby lub podmiotu, który nie powinien ich otrzymać,
* **integralności** – dane zostają nieprawidłowo zmienione, usunięte lub zniekształcone,
* **dostępności** – dane przestają być dostępne wtedy, gdy są potrzebne.

Jedno zdarzenie może naruszać jednocześnie więcej niż jedną właściwość.

Klasyfikacja ta pozwala oddzielić techniczny charakter zdarzenia od jego znaczenia dla ochrony informacji.

---

# 8. Ryzyko pierwotne i rezydualne

Projekt rozróżnia dwa stany ryzyka.

**Ryzyko pierwotne** opisuje sytuację przed uwzględnieniem konkretnych zabezpieczeń.

**Ryzyko rezydualne** opisuje sytuację po ich zastosowaniu.

Rozróżnienie jest istotne, ponieważ samo istnienie ryzyka nie oznacza niezgodności. Zadaniem administratora jest rozpoznanie ryzyka, zastosowanie adekwatnych środków i świadoma ocena tego, co pozostaje.

Dlatego końcowym elementem procesu nie jest samo wyliczenie poziomu ryzyka, ale jego **akceptacja, akceptacja warunkowa albo brak akceptacji**.

Brak akceptacji oznacza konieczność dalszego działania. Akceptacja warunkowa oznacza, że ryzyko może być tolerowane przy spełnieniu określonych warunków lub wykonaniu zaplanowanych działań.

---

# 9. Zabezpieczenia

Zabezpieczenia są traktowane jako osobna warstwa modelu.

Nie są jedynie opisem środków technicznych. Obejmują zarówno środki:

* techniczne,
* organizacyjne,
* proceduralne,
* fizyczne,
* związane z personelem i uprawnieniami.

Dzięki temu jedno zabezpieczenie może być wykorzystane jako odpowiedź na wiele różnych ryzyk.

Istotne jest rozróżnienie:

**wymaganie dotyczące zabezpieczenia → zdefiniowane zabezpieczenie → jego zastosowanie → ocena skuteczności.**

Szczegółowe parametry techniczne nie muszą być umieszczane w każdej procedurze. Są centralizowane w standardzie zabezpieczeń technicznych i organizacyjnych, aby uniknąć powielania i sprzeczności.

---

# 10. DPIA jako pogłębienie analizy

Ocena skutków dla ochrony danych (DPIA) nie jest traktowana jako standardowy dokument wymagany dla każdego procesu.

Najpierw identyfikowane jest przetwarzanie i wykonywana jest analiza potrzeby przeprowadzenia DPIA.

Dopiero gdy charakter przetwarzania i poziom ryzyka uzasadniają taki obowiązek, wykonywana jest właściwa DPIA.

Logika jest więc następująca:

**proces → kwalifikacja do DPIA → w razie potrzeby DPIA.**

Pozwala to zachować ślad świadomej oceny obowiązku również wtedy, gdy końcowy wniosek brzmi: DPIA nie jest wymagana.

---

# 11. Dokumentacja jako kilka różnych klas informacji

Nie wszystkie elementy systemu nazywane są „dokumentami” w tym samym znaczeniu.

Rozróżnienie wynika z ich funkcji i sposobu przechowywania.

### Dokumenty normatywne

Określają, **jak system ma działać**.

Należą tutaj przede wszystkim polityki, standardy i procedury.

Polityka określa zasady i kierunek działania. Standard uszczegóławia wymagania. Procedura opisuje sposób postępowania w określonej sytuacji.

### Dokumenty indywidualne

Dokumentują konkretną decyzję albo zdarzenie.

Są to m.in. umowy, uzgodnienia, protokoły i upoważnienia.

### Rejestry danych i rejestry relacji

Dokumentują **stan albo historię rzeczywistych zdarzeń**.

Przede wszystkim pozwalają wykazać, co faktycznie się wydarzyło, jakie cechy spełnia lub jakie ma relacje z innymi dokumentami systemu.

### Szablony

Nie dokumentują żadnego zdarzenia.

Stanowią wzorcame, z których dopiero powstaje konkretny dokument.

### Checklisty

Pełnią rolę kontrolną.

Ich zadaniem jest zapewnienie, że określony proces, kontrola lub przegląd został wykonany kompletnie i w sposób powtarzalny.

---

# 12. Różnice pomiędzy polityką, standardem i procedurą

W projekcie przyjęto hierarchię:

**polityka → standard → procedura.**

Polityka odpowiada przede wszystkim na pytanie:

**„jakie zasady obowiązują?”**

Standard:

**„jakie minimalne wymagania muszą zostać spełnione?”**

Procedura:

**„co należy zrobić w określonej sytuacji?”**

Przykładowo ogólna polityka bezpieczeństwa nie powinna zawierać wszystkich parametrów technicznych. Parametry takie jak wymagania dotyczące uwierzytelniania, aktualizacji, szyfrowania czy kopii zapasowych mogą być utrzymywane w standardzie technicznym.

Dzięki temu zmiana wymagania technicznego nie wymusza przepisywania wielu niezależnych polityk i procedur.

---

# 13. System informatyczny, procesor i proces

Projekt celowo nie utożsamia tych pojęć.

**Proces** opisuje, dlaczego i w jakim kontekście dane są przetwarzane.

**System** opisuje narzędzie lub środowisko, w którym przetwarzanie jest realizowane.

**Procesor** opisuje podmiot zewnętrzny przetwarzający dane w imieniu administratora.

Jeden proces może korzystać z wielu systemów.

Jeden system może obsługiwać wiele procesów.

Jeden procesor może dostarczać jeden lub kilka systemów lub usług.

Rozdzielenie tych pojęć zapobiega uzależnieniu modelu ochrony danych od aktualnej architektury informatycznej.

---

# 14. Incydent i naruszenie ochrony danych

Projekt świadomie rozróżnia **incydent** od **naruszenia ochrony danych osobowych**.

Incydent oznacza zdarzenie wymagające analizy z punktu widzenia bezpieczeństwa lub prawidłowego działania systemu.

Dopiero analiza incydentu pozwala stwierdzić, czy doszło do naruszenia ochrony danych. Przy czym projekt stosuje definicje incydentu zgodną z RODO: incydent staje się naruszeniem ochrony danych osobowych, jeżeli w jego wyniku faktycznie doszło do naruszenia poufności, integralności lub dostępności danych osobowych.

Logika procesu jest więc następująca:

**zdarzenie → incydent → analiza → kwalifikacja → ewentualne naruszenie → ocena ryzyka dla osób → odpowiednie działania.**

Pozwala to rejestrować również zdarzenia, które ostatecznie nie stanowią naruszenia RODO.

---

# 15. Backup, archiwizacja, retencja i usuwanie

Pojęcia te są powiązane, ale nie są synonimami.

**Backup** służy przede wszystkim odtworzeniu danych po awarii lub utracie.

**Archiwizacja** służy długoterminowemu zachowaniu danych, które muszą pozostać dostępne mimo zakończenia bieżącego wykorzystania.

**Retencja** odpowiada na pytanie, jak długo dane powinny lub mogą być przechowywane.

**Usuwanie** jest końcem cyklu życia danych, gdy dalsze przechowywanie nie ma podstawy lub jest niedopuszczalne.

Dlatego samo wykonywanie backupu nie realizuje polityki archiwizacji, a posiadanie archiwum nie rozwiązuje kwestii retencji.

---

# 16. Udostępnianie dokumentacji medycznej

Udostępnienie dokumentacji jest traktowane jako kontrolowany proces, ponieważ wymaga ustalenia:

* komu dokumentacja została udostępniona,
* na jakiej podstawie,
* czego dotyczył zakres udostępnienia,
* w jaki sposób została przekazana,
* kiedy nastąpiło udostępnienie.

Dlatego proces posiada własną procedurę oraz ewidencję faktycznych udostępnień.

Procedura odpowiada na pytanie **jak należy udostępniać**, a wykaz udostępnionej dokumentacji – **co rzeczywiście udostępniono**.

---

# 17. Upoważnienia

Upoważnienie jest traktowane jako indywidualny dokument określający zakres dopuszczenia konkretnej osoby do przetwarzania danych.

Należy odróżnić:

* wzór upoważnienia,
* konkretne wydane upoważnienie,
* rejestr osób upoważnionych.

Są to trzy różne poziomy informacji.

Analogicznie upoważnienie udzielane przez pacjenta osobie trzeciej jest odrębnym instrumentem od upoważnienia personelu do przetwarzania danych.

Konkretnie wydane upoważnienia są ewidencjonowane w rejrestrze osób uprawnionych.

---

# 18. Harmonogram zgodności

Nie wszystkie obowiązki powinny być realizowane według jednego kalendarza.

Projekt rozróżnia trzy zasadnicze mechanizmy uruchamiania działań.

### Cykliczne

Realizowane np. miesięcznie, kwartalnie, półrocznie lub rocznie.

Służą przede wszystkim kontroli i utrzymaniu systemu.

### Zdarzeniowe

Uruchamiane przez określone zdarzenie, np. incydent, żądanie pacjenta, zmianę procesora albo konieczność udostępnienia dokumentacji.

### Po zmianie

Dotyczą elementów, których nie ma sensu sztucznie wykonywać co miesiąc lub co rok.

Powstają przy uruchomieniu systemu, a następnie są aktualizowane po istotnej zmianie.

Jest to szczególnie ważne dla dokumentów opisujących stan systemu. Sam upływ czasu nie musi oznaczać konieczności ich ponownego tworzenia.

---

# 19. Tabela zgodności jako mapa obowiązków

Lista zgodności nie jest listą dokumentów.

Obejmuje trzy różne rodzaje elementów:

**Dokument** – coś, co powinno istnieć jako utrzymywana informacja.

**Działanie** – coś, co należy wykonać.

**Wymaganie** – stan lub warunek, który musi być spełniony.

Rozróżnienie zapobiega częstemu błędowi polegającemu na utożsamieniu zgodności z posiadaniem odpowiedniego pliku.

Przykładowo posiadanie polityki backupu nie jest równoważne z wykonywaniem backupu ani z potwierdzeniem możliwości odtworzenia danych.

---

# 20. Rejestry jako dowód działania systemu

Rejestry mają szczególne znaczenie, ponieważ łączą projektowany model z rzeczywistym funkcjonowaniem praktyki.

Polityka może stwierdzać, że wykonywane są przeglądy uprawnień.

Dopiero zapis wykonania przeglądu pozwala jednak wykazać, że rzeczywiście został przeprowadzony.

Dlatego projekt rozdziela:

**regułę → działanie → zapis wykonania.**

Nie każda czynność wymaga osobnego rejestru, ale działania istotne dla rozliczalności powinny pozostawiać odpowiedni ślad.

---

# 21. Minimalizacja dokumentacji

Projekt nie zakłada tworzenia osobnego dokumentu dla każdego wymagania RODO.

Nowy dokument jest uzasadniony wtedy, gdy przynajmniej jedno z poniższych jest prawdziwe:

* ma odrębny cel,
* ma odrębny cykl życia,
* jest aktualizowany niezależnie od pozostałych,
* stanowi odrębny dowód wykonania obowiązku,
* jego połączenie z innym dokumentem utrudniałoby utrzymanie systemu.

W przeciwnym przypadku preferowane jest wykorzystanie istniejącej struktury.

Celem jest **minimalny kompletny system**, a nie minimalna liczba plików ani maksymalna liczba dokumentów.

---

# 22. Jedno źródło prawdy

Informacja, która może się zmieniać i jest wykorzystywana w wielu miejscach, powinna mieć możliwie jedno źródło.

Pozostałe elementy powinny się do niej odnosić, a nie tworzyć własne niezależne kopie.

Zasada ta ma znaczenie nie tylko techniczne, lecz przede wszystkim organizacyjne.

Największym zagrożeniem dla długoterminowej użyteczności dokumentacji jest sytuacja, w której kilka dokumentów opisuje ten sam fakt inaczej.


---

# 23. Logika zmian

Zmiana jednego elementu powinna powodować analizę jej konsekwencji dla elementów zależnych.

Przykładowo pojawienie się nowego systemu może wymagać sprawdzenia:

**system → procesy korzystające z systemu → procesor → RCP → ryzyka → zabezpieczenia → umowy → dokumentacja informacyjna.**

Nie oznacza to, że wszystkie te elementy zawsze wymagają zmiany.

Oznacza natomiast, że powinny zostać **sprawdzone**.

Projekt jest więc oparty bardziej na propagacji znaczenia zmiany niż na mechanicznym „aktualizowaniu wszystkich dokumentów”.

---

# 24. Rozliczalność jako zasada spinająca projekt

Całość modelu można sprowadzić do czterech pytań:

**Co robimy?**

Opisują to procesy, RCP, systemy i relacje.

**Dlaczego uważamy, że robimy to prawidłowo?**

Opisują to podstawy prawne, analiza ryzyka, DPIA, polityki, standardy i zabezpieczenia.

**Czy rzeczywiście robimy to w zadeklarowany sposób?**

Pokazują to rejestry, wykazy, checklisty, przeglądy i zapisy zdarzeń.

**Co robimy, kiedy rzeczywistość odbiega od założonego modelu?**

Odpowiadają na to procedury incydentów, naruszeń, działań korygujących i aktualizacji systemu.

To właśnie ten mechanizm, a nie liczba posiadanych dokumentów, stanowi zasadniczą logikę projektu.

---

# 25. Sens całej konstrukcji

Projekt nie ma być „teczką RODO”.

Ma być **modelem zarządzania ochroną danych**, w którym można przejść w obie strony pomiędzy rzeczywistością a dokumentacją.

Dla konkretnego procesu powinno być możliwe ustalenie:

**proces → dane → system → procesor → ryzyko → zabezpieczenie → procedura → działanie → zapis.**

I odwrotnie, dla konkretnego zdarzenia lub dokumentu powinno być możliwe ustalenie:

**dlaczego ten element istnieje, jakiego procesu dotyczy, jakie ryzyko lub obowiązek obsługuje i jakie znaczenie ma dla całego systemu.**

Jeżeli po kolejnych zmianach projektu takie przejście nadal jest możliwe, model zachowuje spójność.

Jeżeli natomiast zaczynają powstawać dokumenty, pola, rejestry lub działania, dla których trudno odpowiedzieć na pytanie **„z czego to wynika i czemu służy?”**, jest to sygnał, że struktura zaczyna obrastać w elementy nieuzasadnione albo utraciła czytelność.

To kryterium powinno być podstawowym testem przy dalszym rozwijaniu projektu.


---

# 26. Szablony dokumentacji

Zasadniczo projekt rozróżnia trzy typy dokumentacji:

- dokumenty normatywne
- wzory dokumentów indywidualnych
- dokumenty indywidualne

Wszystkie te dokumenty mogą zawierać zastępcze teksty, które należy zamienić na docelowe np. imię i nazwisko administratora, adres itd. Wszystkie one mają format [RODO: xxx]. 

Docelowe dokumenty nie powinny zawierać tego typu pól - powinny one zostać zastąpione faktycznymi informacjami.