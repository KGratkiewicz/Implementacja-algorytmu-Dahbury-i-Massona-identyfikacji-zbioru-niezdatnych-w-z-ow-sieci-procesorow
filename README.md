# Implementacja algorytmu Dahbury i Massona identyfikacji zbioru niezdatnych węzłów sieci procesorów w systemie t-diagnozowalnym. 

Notatnik Colaboratory: https://colab.research.google.com/drive/1upOk8wsv6WE-Tl7jMtjc4H5nksdMLB0s?usp=sharing

## Pojęcia podstawowe

### System t-diagnozowalny
System t-diagnozowalny - system będący w stanie wykryć t-uszkodzeń, pod warunkiem, że t/2 >= N gdzie N jest całkowitą liczbą węzłów w systemie.

System jest jednokrokowo t–diagnozowalny, jeżeli wszystkie uszkodzone jednostki systemu mogą być zlokalizowane na podstawie jednego syndromu wyników testowania, o ile liczba aktualnie uszkodzonych jednostek nie przekracza t

System jest wielokrokowo t-diagnozowalny, jeżeli co najmniej jedna niezdatna jednostka może być zlokalizowana na podstawie jednego syndromu wyników testowania, o ile liczba aktualnie uszkodzonych jednostek nie przekracza t. 

### Graf t-diagnozowalny
Graf t-diagnozowalny to reprezentacja grafowa systemu t-diagnozowalnego reprezentowana przez graf skierowany.

𝐺 =⟨𝑉; 𝐸⟩ 

gdzie: 
𝑉 – proces systemu
𝐸 – podzbiór iloczynu kartezjańskiego 𝑉×𝑉 (krawędź skierowana pomiędzy dwoma wierzchołkami)


### Syndrom

Syndrom jest to wynik testu z przedziału {0,1} gdzie 0 oznacza sukces a 1 oznacza porażkę wraz z przypisaną krawędzią garfu t-diagnozowalnego.

## Algorytm Dahbury i Massona

Dany jest graf t-diagnozowalny G, przedstawiający przedział testów, oraz dany jest syndrom S.

Na podstawie G i S określany jest graf zwykły 

L(G,S) =⟨𝑉; 𝐸𝐿 ⟩ 

gdzie:

𝐸𝐿={(𝑒𝑖,𝑒𝑗 )|𝑒𝑗∈𝐿(𝑒𝑖)}  , a 𝐿(𝑒𝑖) jest zbiorem takich jednostek, które mogą być określone poprzez dedukcję jako niezdatne przy założeniu, że 𝑒𝑖 jest zdatna.

Po uzyskani grafu L(G), należy określić zbiory:

K*  - minimalny podzbiór węzłów (pokrycie) – każda krawędź grafu L jest incydentna z co najmniej jednym węzłem z K* (minimalny zbiór zewnętrznie stabilny)

M* - maksymalny podzbiór krawędzi stanowiący dopasowanie – każdy węzeł grafu L jest incydentny z co najwyżej jedną krawędzią M*

Następnie należy określić maksymalne skojarzenie zbiorów K* i M* - ostatecznie zbiór węzłów oznacza węzły uszkodzone, które należy wymienić.

## Wyznaczenie syndromu grafu
Syndorm wyznaczany jest za pomocą nasyępującego algorytmu:
*   Jeżeli połączenie między wierzchołkami nie istnieje: -1
*   Jeżeli wierzchołek początkowy jest sprawny i końcowny jest sprawny: 0
*   Jeżeli wierzchołek początkowy jest sprawny i końcowny jest uszkodzony: 1
*   Jeżeli wierzchołek początkowy jest uszkodzony: losuj z pa= 0.5 wartość 0 lub 1 

## Algorytm Dahbury i Massona

### Graf 2-diagnozowalny
![image](https://user-images.githubusercontent.com/71324202/232430236-1e5e849e-5fb8-49cf-8a77-12067b5e3ea4.png)

### Graf testów z syndromem
![image](https://user-images.githubusercontent.com/71324202/232429529-d742ecd2-54c7-420b-a5ba-73dd9f29d100.png)

### L-graf (dedukcji)
![image](https://user-images.githubusercontent.com/71324202/232429607-b4397b9b-d50b-4f8a-84bf-802829fcef0c.png)

### Wyznaczenie zbioru K
![image](https://user-images.githubusercontent.com/71324202/232429848-cd9d850b-f58e-4aef-b44e-302b4d767307.png)

### Wyznaczenie zbioru M
![image](https://user-images.githubusercontent.com/71324202/232429924-955ec507-9ff9-49de-9e5e-35bc7f59d78e.png)


### Wyznaczenie skojarzenia K i M: {1, 3}

