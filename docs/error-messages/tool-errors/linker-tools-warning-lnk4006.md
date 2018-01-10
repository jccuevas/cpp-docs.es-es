---
title: Las herramientas del vinculador LNK4006 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4006
dev_langs: C++
helpviewer_keywords: LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 021961029d274172119ae92aa10cc6a236dd973b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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