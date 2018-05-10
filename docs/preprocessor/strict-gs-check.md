---
title: strict_gs_check | Documentos de Microsoft
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
ms.openlocfilehash: 6b58b02781f266b24fa321b3849f42b2e090b860
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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
 Indica al compilador que inserte una cookie aleatoria en la pila de la función para ayudar a detectar algunas categorías de saturación del búfer basada en la pila. De forma predeterminada, la opción de compilador /GS (comprobación de seguridad del búfer) no inserta una cookie para todas las funciones. Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md).  
  
 Debe compilar con /GS (comprobación de seguridad del búfer) para habilitar strict_gs_check.  
  
 Utilice esta directiva pragma en módulos que estén expuestos a datos potencialmente dañinos. Esta directiva pragma es muy agresiva y se aplica a funciones que quizá no necesiten esta defensa, pero está optimizada para minimizar su efecto sobre el rendimiento de la aplicación resultante.  
  
 Incluso si usa esta directiva pragma, debe procurar escribir código seguro. Es decir, asegúrese de que el código no tenga ninguna saturación de búfer. strict_gs_check puede proteger la aplicación de saturaciones del búfer que permanecen en el código.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente, se produce una saturación del búfer cuando copiamos una matriz en una matriz local. Cuando se compila este código con /GS, no se inserta ninguna cookie de la pila, porque el tipo de datos de la matriz es un puntero. Al agregar la directiva pragma strict_gs_check se fuerza la cookie de la pila en la pila de funciones.  
  
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