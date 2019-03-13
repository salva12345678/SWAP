## Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).

Aplicamos las fórmula **As=Acn-1 + ((1-Acn-1)x Acn)**

Aweb=0.85+((1-0.85) x 0.9775)=0.996625

Aaplications=0.90+((1-0.90) x 0.99)=0.999

Adatabase=0.999+((1-0.999) x 0.999999)=0.99999999

Adns=0.98+((1-0.98) x 0.9996)=0.999992

Afirewall=0.85+((1-0.85) x 0.9775)=0.996625

Aswitch=0.99+((1-0.99) x 0.9999)=0.999999

Adatacenter=0.9999

Aisp=0.95+((1-0.95) x 0.9775)=0.999875

As= 0.996625 x 0.999 x 0.99999999 x 0.999992 x 0.996625 x 0.999999 x 0.9999 x 0.999875

**AsTotal=0.992035**
