# Tema-1-PCom
Tema 1 Protocoale de Comunicatii 2024
~ Subcerinte rezolvate: toate

~ Flow:

- Initializarea: Programul incepe prin initializarea variabilelor si a
  structurilor de date necesare, inclusiv a tabelului de rutare, a tabelei
  ARP si a cozii de asteptare a pachetelor.
- Citirea tabelei de rutare: Programul citeste tabela de rutare din fisierul
  specificat in linia de comanda si o incarca in memorie.
- Construirea trie-ului: Se construieste un trie pentru a eficientiza cautarea
  celei mai lungi potriviri (LPM) in tabela de rutare.
- Primire pachete: Programul asteapta primirea unui pachet de la orice interfata
  de retea.
- Verificarea tipului de pachet: Daca pachetul este de tip ARP, se verifica daca
  adresa IP de destinatie apartine routerului si se gestioneaza cererea ARP
  corespunzator. Daca pachetul este de tip IPv4, se efectueaza verificari pentru
  asigurarea integritatii si a TTL-ului.
- Cautare drum in tabela de rutare: Se utilizeaza trie-ul pentru a gasi cea mai
  lunga potrivire in tabela de rutare pentru adresa IP de destinatie a
  pachetului.
- Trimitere pachet: Daca ruta este gasita, pachetul este trimis la interfata
  corespunzatoare cu adresa MAC a urmatorului hop. Daca ruta nu poate fi gasita,
  se trimite un mesaj ICMP de "Destination Unreachable".
- Actualizare ARP: Daca nu exista o intrare ARP pentru urmatorul hop, se trimite
  o cerere ARP si pachetul este pus in coada de asteptare. Dupa primirea unui
  raspuns ARP, adresa MAC este retinuta si pachetele aflate in coada sunt
  procesate.
- Repetare: Procesul se repeta continuu, asigurand rutarea corecta a pachetelor
  IPv4 in retea.


In implementarea mea, am folosit o structura modulara pentru a gestiona rutarea
pachetelor IPv4 in retea. Am utilizat o trie pentru a eficientiza cautarea celei
mai lungi potriviri in tabela de rutare, imbunatatind performantele in
comparatie cu o cautare liniara. Am implementat procesul de dirijare folosind
pasii specificati pentru IPv4, inclusiv verificarea integritatii pachetelor si
a TTL-ului.

Pentru protocolul ARP, am implementat functionalitatea de asteptare a unui ARP
Reply pentru a popula dinamic tabela ARP. Am folosit o coada pentru a gestiona
pachetele care asteapta un raspuns ARP si am actualizat cache-ul ARP dupa
primirea unui raspuns.

Pentru ICMP, am implementat functionalitatea de gestionare a mesajelor de eroare
ICMP, inclusiv trimiterea de mesaje "Time Exceeded" si "Destination Unreachable"
in functie de contextul rutei pachetului.
