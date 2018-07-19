---
title: -INTERVALO DE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d06d699500ba3ea441af61a2e2a5a0da3f96903a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374429"
---
# <a name="range"></a>/RANGE
Modifica el resultado de dumpbin cuando se utiliza con otras opciones de dumpbin, como /RAWDATA o/DISASM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Marcas  
 **vaMin**  
 La dirección virtual a la que desea que comience la operación dumpbin.  
  
 **vaMax** (opcional)  
 La dirección virtual en el que desea que la operación dumpbin para finalizar. Si no se especifica, dumpbin irá al final del archivo.  
  
## <a name="remarks"></a>Comentarios  
 Para ver las direcciones virtuales para una imagen, use el archivo de asignación de la imagen (RVA + Base), el **/DISASM** o **/HEADERS** opción de dumpbin, o la ventana Desensamblado en el depurador de Visual Studio.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, **/rango** se utiliza para modificar la presentación de la **/DISASM** opción. En este ejemplo, el valor inicial se expresa como un número decimal y el valor final se especifica como un número hexadecimal.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)