---
title: Generar excepciones de Software | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb616945a831502077066bdf306bef306f543eb
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="raising-software-exceptions"></a>Generar excepciones de software
El sistema no marca como excepciones algunos de los orígenes de errores de programa más comunes. Por ejemplo, si intenta asignar un bloque de memoria pero no hay memoria insuficiente, el tiempo de ejecución o la función de API no provoca una excepción, sino que devuelve un código de error.  
  
 Sin embargo, puede tratar cualquier condición como excepción detectando esa condición en el código y comunicándolo a continuación mediante una llamada a la [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) función. Si marca los errores de esta manera, puede aportar las ventajas del control de excepciones estructurado a cualquier tipo de error en tiempo de ejecución.  
  
 Para usar el control de excepciones estructurado con errores:  
  
-   Defina su propio código de excepción para el evento.  
  
-   Llame a **RaiseException** cuando detecte un problema.  
  
-   Use filtros de control de excepciones para probar el código de excepción definido.  
  
 El \<winerror.h > archivo muestra el formato de códigos de excepción. Para asegurarse de que no define un código en conflicto con un código de excepción existente, establezca el tercer bit más significativo en 1. Los cuatro bits más significativos se deben establecer como se muestra en la tabla siguiente.  
  
|Bits|Valor binario recomendado|Descripción|  
|----------|--------------------------------|-----------------|  
|31-30|11|Estos dos bits describen el estado básico del código: 11 = error, 00 = correcto, 01 = informativo, 10 = advertencia.|  
|29|1|Bit de cliente. Establézcalo en 1 para los códigos definido por el usuario.|  
|28|0|Bit reservado. (Déjelo establecido en 0).|  
  
 Puede establecer los dos primeros bits en un valor distinto del binario 11 si lo desea, aunque el valor de “error” es adecuado para la mayoría de las excepciones. Lo importante es recordar establecer los bits 29 y 28 como se muestra en la tabla anterior.  
  
 El código de error resultante debe tener por lo tanto, los cuatro bits superiores establecidos en e hexadecimal. Por ejemplo, las definiciones siguientes definen códigos de excepción que no entren en conflicto con ningún código de excepción de Windows. (Es posible, no obstante, que deba comprobar qué códigos usan los archivos DLL de terceros).  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 Después de definir un código de excepción, puede usarlo para provocar una excepción. Por ejemplo, el código siguiente provoca la excepción de STATUS_INSUFFICIENT_MEM en respuesta a un problema de asignación de memoria:  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 Si desea generar simplemente una excepción, puede establecer los tres últimos parámetros en 0. Los tres últimos parámetros son útiles para pasar información adicional y establecer una marca que evite que los controladores continúen la ejecución. Consulte la [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) funcionando en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] para obtener más información.  
  
 En los filtros de control de excepciones, puede probar los códigos que haya definido. Por ejemplo:  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)