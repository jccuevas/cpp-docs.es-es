---
title: Las herramientas del vinculador LNK4006 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 261d5dcc27c44291ddc6de4a6440cde040a84ed7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4006"></a>Advertencia de las herramientas del vinculador LNK4006
símbolo ya definido en el objeto; segunda definición omitida  
  
 El `symbol` proporcionado, que se muestra en su forma representativa, se definió varias veces. Cuando se produce esta advertencia, `symbol` se agregarán dos veces, pero se utilizará sólo el primer formulario.  
  
 Puede obtener esta advertencia si se intenta combinar dos bibliotecas de importación en uno.  
  
 Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede omitir este mensaje.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  El determinado `symbol` puede ser una función empaquetada, creada al compilar con [/Gy](../../build/reference/gy-enable-function-level-linking.md). Este símbolo se incluyó en más de un archivo, pero se ha cambiado entre las compilaciones. Vuelva a compilar todos los archivos que incluyen la `symbol`.  
  
2.  El determinado `symbol` pueden haber sido definidas diferente en dos objetos miembro de diferentes bibliotecas.  
  
3.  Absoluto puede haber sido definido dos veces, con un valor diferente en cada definición.  
  
4.  Si se recibe el mensaje de error al combinar bibliotecas, `symbol` ya existe en la biblioteca que se va a agregar a.