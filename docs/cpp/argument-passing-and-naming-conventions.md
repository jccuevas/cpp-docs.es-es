---
title: Paso de argumentos y convenciones de nomenclatura | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43aa3430b641f6333c6c35d618f9e9de123b7390
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413491"
---
# <a name="argument-passing-and-naming-conventions"></a>Paso de argumentos y convenciones de nomenclatura
**Específicos de Microsoft**  
  
 Los compiladores de Visual C++ permiten especificar convenciones para pasar argumentos y valores devueltos entre funciones y llamadores. No todas las convenciones están disponibles en todas las plataformas compatibles y algunas convenciones utilizan implementaciones específicas de la plataforma. En la mayoría de los casos, se omiten palabras clave o modificadores de compilador que especifican una convención no compatible en una plataforma concreta y se usa la convención predeterminada de la plataforma.  
  
 En plataformas x86, todos los argumentos se amplían a 32 bits cuando se pasan. Los valores devueltos también se amplían a 32 bits y se devuelven en el registro EAX, salvo las estructuras de 8 bytes, que se devuelven en el par de registros EDX:EAX. Las estructuras de mayor tamaño se devuelven en el registro EAX como punteros a estructuras de devolución ocultas. Los parámetros se insertan en la pila de derecha a izquierda. Las estructuras distintas de POD no se devolverán en registros.  
  
 El compilador genera código de prólogo y epílogo para guardar y restaurar los registros ESI, EDI, EBX y EBP, si se usan en la función.  
  
> [!NOTE]
>  Cuando se devuelve un struct, una unión o una clase desde una función por valor, todas las definiciones del tipo deben ser iguales; de lo contrario, se puede producir un error en el programa en tiempo de ejecución.  
  
 Para obtener información sobre cómo definir su propio código de prólogo y epílogo de la función, vea [llamadas a funciones Naked](../cpp/naked-function-calls.md).  
  
 Para obtener información sobre el valor predeterminado convenciones de llamada en el código que vea plataformas de destinos x64, [información general sobre x64 convenciones de llamada](../build/overview-of-x64-calling-conventions.md). Para obtener información acerca de problemas de la convención de llamada en el código que tiene como destino plataformas ARM, vea [problemas comunes de migración de ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md).  
  
 El compilador de Visual C/C++ admite las siguientes convenciones de llamada.  
  
|Palabra clave|Limpieza de la pila|Paso de parámetros|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|Llamador|Inserta parámetros en la pila, en orden inverso (de derecha a izquierda)|  
|[__clrcall](../cpp/clrcall.md)|N/D|Carga parámetros en la pila de expresiones CLR en orden (de izquierda a derecha).|  
|[__stdcall](../cpp/stdcall.md)|Destinatario|Inserta parámetros en la pila, en orden inverso (de derecha a izquierda)|  
|[__fastcall](../cpp/fastcall.md)|Destinatario|Almacenado en los registros y luego insertado en la pila|  
|[__thiscall](../cpp/thiscall.md)|Destinatario|Inserta en la pila; **esto** puntero almacenado en ECX|  
|[__vectorcall](../cpp/vectorcall.md)|Destinatario|Almacenado en registros y luego insertado en la pila en orden inverso (de derecha a izquierda)|  
  
 Para obtener información relacionada, consulte [convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)