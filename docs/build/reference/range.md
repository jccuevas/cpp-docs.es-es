---
title: -INTERVALO DE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ccca814a388a458513773247f79cecf87fcdeae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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