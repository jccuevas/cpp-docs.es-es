---
title: "Asignaci&#243;n de espacio de pila | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Asignaci&#243;n de espacio de pila
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El prólogo de una función es responsable de asignar espacio de pila para variables locales, registros guardados, parámetros de pila y parámetros de registro.  
  
 El área de parámetros siempre está al final de la pila \(incluso si se usa alloca\), de modo que siempre estará adyacente a la dirección devuelta durante una llamada a cualquier función.  Contiene por lo menos cuatro entradas, pero siempre hay suficiente espacio para contener todos los parámetros que pueda necesitar una función a la que se pueda llamar.  Tenga en cuenta que siempre se asigna espacio para los parámetros de registro, incluso si estos parámetros nunca se hospedan en la pila; se puede tener la seguridad de que una función llamada siempre tendrá espacio asignado para todos sus parámetros.  Los argumentos de registro requieren direcciones iniciales, por lo tanto, hay un área contigua disponible por si la función llamada necesitase tomar la dirección de la lista de argumentos \(va\_list\) o un argumento concreto.  Esta área también es un lugar apropiado para guardar argumentos de registro durante la ejecución de código thunk y como opción de depuración \(por ejemplo, hace que sea fácil localizar los argumentos durante la depuración si están almacenados en sus direcciones iniciales en el código de prólogo\).  Aunque la función llamada tenga menos de 4 parámetros, estas 4 ubicaciones de la pila pertenecen de manera efectiva a dicha función, que puede utilizarlas para otros fines, además de guardar valores de registro de parámetros.  Así, el llamador no puede guardar información en esta región de la pila durante una llamada a la función.  
  
 Si el espacio se asigna dinámicamente \(alloca\) en una función, se debe utilizar un registro no variable como puntero de marco para marcar la base de la parte fija de la pila, y el registro debe estar guardado e inicializado en el prólogo.  Tenga en cuenta que, cuando se utiliza alloca, las llamadas al mismo destinatario desde el mismo llamador pueden tener direcciones iniciales diferentes para sus parámetros de registro.  
  
 La pila siempre se mantendrá con alineación de 16 bits, excepto en el prólogo \(por ejemplo, después de insertar la dirección devuelta\) y excepto donde se indica en [Tipos de funciones](../build/function-types.md) para una determinada clase de funciones de marco.  
  
 A continuación, se muestra un ejemplo del diseño de pila, donde la función A llama a una función B sin hoja.  El prólogo de la función A ya ha asignado espacio para todos los parámetros de registro y de pila requeridos por la B al final de la pila.  La llamada inserta la dirección de devolución y el prólogo de B asigna espacio para sus variables locales, registros no variables y el espacio necesario para que pueda llamar a funciones.  Si B utiliza alloca, el espacio se asigna entre el área para guardar variables locales y registros no variables y el área de la pila para parámetros.  
  
 ![Ejemplo de conversión AMD](../build/media/vcamd_conv_ex_5.png "vcAmd\_conv\_ex\_5")  
  
 Cuando la función B llama a otra función, la dirección de devolución se inserta justo debajo de la dirección inicial para RCX.  
  
## Vea también  
 [Uso de las pilas](../build/stack-usage.md)