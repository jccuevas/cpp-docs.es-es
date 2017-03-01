---
title: Escribir manipuladores propios sin argumentos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 276bba3dd5ce5debd926ebbc4ccfaf52c6b92097
ms.lasthandoff: 02/24/2017

---
# <a name="writing-your-own-manipulators-without-arguments"></a>Escribir manipuladores propios sin argumentos
Escribir manipuladores que no usan argumentos no requiere la derivación de clases ni el uso de macros complejas. Supongamos que su impresora requiere el par \<ESC >[ para entrar en modo de negrita. Puede insertar este par directamente en la secuencia:  
  
```  
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;  
```  
  
 O puede definir el manipulador `bold`, que inserta los caracteres:  
  
```  
ostream& bold(ostream& os) {  
    return os <<'\033' <<'[';  
}  
cout <<"regular " <<bold <<"boldface" <<endl;  
```  
  
 La función `bold` definida globalmente toma un argumento de referencia `ostream` y devuelve la referencia `ostream`. No es una función miembro ni una función friend porque no necesita tener acceso a los elementos de ninguna clase privada. La función `bold` se conecta a la secuencia porque el operador `<<` de la secuencia se sobrecarga para aceptar este tipo de función, mediante una declaración de aspecto similar al siguiente:  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     // call ios_base manipulator  
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}  
```  
  
 Puede usar esta característica para ampliar otros operadores sobrecargados. En este caso, que `bold` inserte caracteres en la secuencia es algo eventual. La función se llama cuando se inserta en la secuencia, no necesariamente cuando se imprimen los caracteres adyacentes. Por tanto, la impresión podría retrasarse debido al almacenamiento en búfer de la secuencia.  
  
## <a name="see-also"></a>Vea también  
 [Flujos de salida](../standard-library/output-streams.md)


