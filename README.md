# Tanky Car Racing

Tanky Car Racing este un joc de simularea in mod realist a unei curse de masini. Acestea sunt dotate cu un tun ce lanseaza proiectile care, daca nimeresc adversarul, il incetinesc si il destabilizeaza. Jocul a fost realizat in totalitate in Unreal Engine 4.

# Controls

  W, A, S, D = modificarea directiilor de mers
*la atingerea unui anumit RPM transmisia schimba automat intr-o treapa superioara
  
  SPACE = frana de mana
 
  F = actionarea tunului

  R = respawn la ultimul checkpoint

  E = aplicarea shader-ului

  TAB = modificarea view-ului
  
# Simularea fizicii tunului si animatii

Cand jucatorul apasa tasta "F", se verifica daca acesta are in inventar un glont. In caz afirmativ, se spawneaza un obiect de tip glont in fata masinii. Pe acest glont este aplicata o forta egala cu directia masinii inmultita cu o constanta. La intrarea in contact cu glontul, masina controlata de AI se opreste pentru 3 secunde si intra intr-o animatie de rotire. Daca glontul scade sub o viteza minima sau intra in contact cu o masina, acesta se despawneaza.

# Car AI

Este un pathfollower, circuitul fiind reprezentat printr-o combinatie de spline-uri

Se obtine tangenta la spline in raport cu locatia masinii. Am normalizat valoarea obtinuta si aceasta va fi folosita de AI in calcularea noii pozitii in care trebuie sa se deplaseze.  
In raport cu aceasta pozitie, calculam unghiul cu care trebuie sa rotim de volan pentru a ne deplasa in directia noii destinatii. Acest procedeu este realizat de fiecare data cand AI-ul se deplaseaza, valoarea returnata reprezentand inputul nivelului de rotatie pentru a ajunge pe traiectoria descrisa de spline.

AI-ul selecteaza in mod automat ce spline sa urmeze in functie de 3 evenimente: 
- prezenta unui drum drept, liber => acceleratie crescanda 
- prezenta unei curbe: => reducere acceleratie si pregatire de franare 
- prezenta unui obstacol => adaptarea vitezei in functie de tipul de obstacol (rampa, speedbumps, etc)

Prin natura sa atat de path-folower cat si path-finder, indiferent daca este lovit in afara pistei sau nimerit cu un proiectil, AI-ul recalculeaza pasii necesari pentru a se intoarce pe circuit si a obtine viteza caracteristica

# Complex Post-Processing Shader

Am folosit un shader de contur pentru a oferi un effect de Vaporwave jocului. Acest effect se activeaza prin apasarea tastei E

Mai multe detalii cu privire la implementare + proof de implementare al task-urilor se gasesc in powerpoint-ul de pe acest git.
