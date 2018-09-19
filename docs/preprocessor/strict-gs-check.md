---
title: strict_gs_check | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5e9ce2480612cdc84982cd1474e003d9151557
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541282"
---
# <a name="strictgscheck"></a>strict_gs_check
Esta directiva pragma proporciona una comprobación de seguridad mejorada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## <a name="remarks"></a>Comentarios  
 
Indica al compilador que inserte una cookie aleatoria en la pila de la función para ayudar a detectar algunas categorías de saturación del búfer basada en la pila. De forma predeterminada, el `/GS` (Buffer Security Check) la opción del compilador no inserta una cookie para todas las funciones. Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md).  
  
Debe compilar con `/GS` (Buffer Security Check) para habilitar **strict_gs_check**.  
  
Utilice esta directiva pragma en módulos que estén expuestos a datos potencialmente dañinos. Esta directiva pragma es muy agresiva y se aplica a funciones que quizá no necesiten esta defensa, pero está optimizada para minimizar su efecto sobre el rendimiento de la aplicación resultante.  
  
Incluso si usa esta directiva pragma, debe procurar escribir código seguro. Es decir, asegúrese de que el código no tenga ninguna saturación de búfer. **strict_gs_check** puede proteger la aplicación las saturaciones del búfer que permanezcan en el código.  
  
## <a name="example"></a>Ejemplo  
 
En el código siguiente, se produce una saturación del búfer cuando copiamos una matriz en una matriz local. Cuando se compila este código con `/GS`, se inserta ninguna cookie en la pila, porque el tipo de datos de matriz es un puntero. Agregar el **strict_gs_check** pragma fuerza la cookie de pila en la pila de la función.  
  
```cpp  
// pragma_strict_gs_check.cpp  
// compile with: /c  
  
#pragma strict_gs_check(on)  
  
void ** ReverseArray(void **pData,  
                     size_t cData)  
{  
    // *** This buffer is subject to being overrun!! ***  
    void *pReversed[20];  
  
    // Reverse the array into a temporary buffer  
    for (size_t j = 0, i = cData; i ; --i, ++j)  
        // *** Possible buffer overrun!! ***  
            pReversed[j] = pData[i];   
  
    // Copy temporary buffer back into input/output buffer  
    for (size_t i = 0; i < cData ; ++i)   
        pData[i] = pReversed[i];  
  
    return pData;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md)