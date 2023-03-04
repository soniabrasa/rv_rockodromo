# Rockodromo

Práctica de un xogo de VR en UNITY con Oculus Quest 2

## Proposta

Realizar un videoxogo Rockodromo, que permita simular unha escalada por unha parede con puntos de agarre, partindo do proxecto base entregado, que xa ten montada a escena con todos os obxectos necesarios, polo que só é necesario programar e configurar os compoñentes que se precisen.

## Funcionamento  

O funcionamento da escalada (ou de outro tipo de movemento por agarre e impulso, como se pode ver, por exemplo, en xogos ambientados en naves espaciais en ingravidez) baséase en medir a velocidade da man que está agarrada a un obxecto fixo e desprazar o xogador coa mesma velocidade pero en sentido contrario.   

O movemento aplicarémolo utilizando un `CharacterController`, que controlaremos dende un script que deberemos crear, chamado *_Climber_*.   

O *_Climber_* deberá controlar cal é a man que está ó mando nun momento dado.  

Temos que ter en conta que as mans se deberán ir alternando e que si nun momento dado non hai ningunha man agarrada deberemos caer.  

Se estamos agarrados con unha soa man, poñamos a diestra, esta será a man ó mando, ou escaladora, e o seu movemento determinará o do xogador.   

No momento en que a outra man (no exemplo a siniestra) se agarre, esta pasará a ser a man escaladora. Pero hai que seguir controlando se a man diestra, cuxos movementos agora son irrelevantes, está ou non agarrada, xa que dependendo diso, ó soltar a man escaladora, a outra man pasará a ser a escaladora se está agarrada, mentres que en caso contrario, o xogador caería ata o chan.   

Para que o *_Climber_* saiba cando unha man agarra ou solta un dos puntos de agarre. Para elo deberemos completar o script `ClimbInteractable` que posúen os obxectos *Knob*.
Este script deberá responder a cada agarre ou solta de un destes obxectos notificando ó *_Climber_* cal é o interactuador que fai esa acción.   

Necesitaremos un compoñente *_HandControllerSpeedometer_* que mida a velocidade da man coma un vector. Realmente o que faremos será obter a velocidade do correspondente mando lendo unha propiedade do mesmo a través do InputSystem de Unity. Esta propiedade deberemos creala usando as ferramentas que Unity nos proporciona para elo.


## Movemento continuo  

Aproveitando que temos xa un `CharacterController` no `XROrigin`, dotaremos a este de movemento continuo. Veremos que esta nova capacidade de movemento non se leva ben coa escalada, o que nos obrigará a buscar unha solución ó problema.
