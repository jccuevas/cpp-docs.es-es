---
title: Error irrecuperable del compilador de recursos RC1120 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d117f7b106e14cde2def5477fab5ad0fc92a6411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Error irrecuperable del compilador de recursos RC1120
memoria insuficiente, necesita el número de bytes  
  
 El compilador de recursos se quedó sin almacenamiento para los elementos que almacena en su montón. Suele ser el resultado de tener demasiados símbolos.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Aumentar el espacio de archivo de intercambio de Windows. Para obtener más información acerca de cómo aumentar el espacio de archivo de intercambio, consulte memoria virtual en la Ayuda de Windows.  
  
2.  Elimine los archivos de inclusión, especialmente que ya no necesarios `#define`prototipos s y la función.  
  
3.  Divida el archivo actual en dos o más archivos y compilarlos por separado.  
  
4.  Quite otros programas o controladores que se ejecutan en el sistema, que podría estar consumiendo una cantidad significativa de memoria.