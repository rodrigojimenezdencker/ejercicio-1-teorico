Ejercicio 1 - Teórico

1. Uno de los problemas que veo es que si se añaden más modalidades de pago o de cobro, se tendría que añadir un if/else if (o switch) 
por cada modalidad.

2. Lo que yo propongo es hacer que Service tenga una función getPrice() que sea heredada por sus hijos
StreamingService y DownloadService (y los que se vayan añadiendo a futuro), y de esta manera
podremos facilmente acceder al precio dependiendo de qué modalidad se trata.
En MultimediaContent haría una función que se llame GetFees() que sea heredada por PremiumContent y
que devuelva el valor de additionalFee.

De esa manera podremos acceder a los precios y a las tarifas adicionales con la función .reducer(), por ejemplo.


class RegisteredUser{

    constructor(services = []){
        this.services = services;
    }
   
    getTotal (){
        let total = 0;

	this.services.reduce((acc, service) => acc + service.getPrice(), total);

        return total;
    }
}
