---
title: Asignación de pila | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22c2afae3678e945678862059034b4d60be456b0
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "32380607"
---
# <a name="stack-allocation"></a>Asignación de espacio de pila
Prólogo de una función es responsable de asignar espacio de pila para las variables locales, registros guardados, los parámetros de la pila y parámetros de registro.  
  
 El área de parámetros está siempre en la parte inferior de la pila (incluso si se usa alloca), de modo que siempre estará adyacente a la dirección de retorno durante cualquier llamada de función. Contiene al menos cuatro entradas, pero siempre espacio suficiente para contener todos los parámetros necesarios para cualquier función que se puede llamar. Tenga en cuenta que siempre se asigna espacio para los parámetros de registro, incluso si los parámetros propios nunca se hospedan en la pila; un destinatario se garantiza que se ha asignado espacio para todos sus parámetros. Direcciones particulares son necesarias para los argumentos del registro para que esté disponible un área contigua en caso de que la función llamada debe tomar la dirección de la lista de argumentos (va_list) o un argumento concreto. Esta área también proporciona un lugar conveniente para guardar los argumentos de registro durante la ejecución de código thunk y como opción de depuración (por ejemplo, hace que los argumentos fáciles de encontrar durante la depuración si están almacenados en sus direcciones de inicio en el código de prólogo). Incluso si la función llamada tiene menos de 4 parámetros, estas ubicaciones de 4 pila eficazmente pertenecen a la función llamada y se pueden usar la función llamada para otros fines además de guardar los valores de registro de parámetro.  Por lo tanto el llamador no puede guardar información en esta región de pila a través de una llamada de función.  
  
 Si el espacio se asigna dinámicamente (alloca) en una función, un registro permanente que debe usarse como un puntero de marco para marcar la base de la parte fija de la pila y ese registro debe guardarse e inicializado en el prólogo. Tenga en cuenta que cuando se utiliza alloca, las llamadas al mismo destinatario desde el mismo llamador pueden tener diferentes direcciones particulares para sus parámetros de registro.  
  
 La pila siempre se mantendrá 16 bytes alineados, excepto en el prólogo (por ejemplo, una vez que se inserta el remite) y, excepto donde se indica en [tipos de función](../build/function-types.md) para una clase determinada de las funciones de marco.  
  
 El siguiente es un ejemplo del diseño de pila donde llamadas de función A una hoja no funcionan prólogo de la función B. la ya ha asignado espacio para todos los parámetros de registro y de pila requeridos por B en la parte inferior de la pila. La llamada inserta el remite y prólogo de B asigna espacio para sus variables locales, los registros no volátiles y el espacio necesario para que pueda llamar a funciones. Si B utiliza alloca, se asigna el espacio entre el registro permanente o variable local área de almacenamiento y el área de la pila de parámetro.  
  
 ![Ejemplo de conversión de AMD](../build/media/vcamd_conv_ex_5.png "vcAmd_conv_ex_5")  
  
 Cuando la función B llama a otra función, se inserta el remite justo debajo de la dirección particular para RCX.  
  
## <a name="see-also"></a>Vea también  
 [Uso de las pilas](../build/stack-usage.md)