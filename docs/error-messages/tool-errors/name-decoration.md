---
title: "Nombre decoración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f780b91d7d58ecdfc9b2af4295c76253357f8e66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="name-decoration"></a>Decoración de nombres
La decoración de nombres normalmente hace referencia a las convenciones de nomenclatura de C++, pero también se puede aplicar a varios casos de C. De forma predeterminada, C++ usa el nombre de la función, los parámetros y el tipo de valor devuelto para crear un nombre del vinculador para la función. Considere la siguiente función:  
  
```  
void CALLTYPE test(void)  
```  
  
 En la tabla siguiente se muestra el nombre del vinculador para varias convenciones de llamada.  
  
|Convención de llamada|archivo de extern "C" o .c|.cpp, .cxx o /TP|  
|------------------------|---------------------------|------------------------|  
|Convención de nomenclatura de C (`__cdecl`)|_test|? probar@ZAXXZ|  
|Convención de nomenclatura de fastcall (`__fastcall`)|@test@0|? probar@YIXXZ|  
|Convención de nomenclatura de llamada estándar (`__stdcall`)|_test@0|? probar@YGXXZ|  
|Convención de nomenclatura de Vectorcall (`__vectorcall`)|probar @@0|? probar@YQXXZ|  
  
 Use extern "C" para llamar a una función de C desde C++. Extern "C" fuerza el uso de la convención de nomenclatura de C para funciones C++ no de clases. Tenga en cuenta modificadores de compilador **/TC** o **/Tp**, que indican al compilador que omita la extensión de nombre de archivo y compile el archivo como C o C++, respectivamente. Estas opciones pueden dar lugar a nombres inesperados.  
  
 Tener prototipos de función con parámetros no coincidentes también puede producir este error. La decoración de nombres incorpora los parámetros de una función en el nombre de función representativo final. Llamar a una función con tipos de parámetro que no coinciden con los de la declaración de función también puede generar el error LNK2001.  
  
 Actualmente, no hay un estándar de denominación entre fabricantes de compiladores, ni entre versiones diferentes de un compilador de C++. Por ello, vincular archivos objeto compilados con otros compiladores puede no producir el mismo esquema de denominación y causar externos sin resolver.  
  
## <a name="see-also"></a>Vea también  
 [Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)