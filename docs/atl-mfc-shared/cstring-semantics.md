---
title: "Semántica de CString | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 394e459a46003e3f1baccff7dd4c76f40b73e354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-semantics"></a>Semántica de CString
Aunque [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos son objetos dinámicos que pueden crecer, actúan como tipos primitivos integrados y clases simples. Cada `CString` objeto representa un valor único. `CString`objetos deben considerarse como las cadenas reales en lugar de punteros a cadenas.  
  
 Puede asignar uno **CString** objeto a otro. Sin embargo, cuando se modifica uno de los dos `CString` objetos, el otro `CString` objeto no se modifica, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 Observe que, en el ejemplo que los dos `CString` objetos se consideran "iguales a", ya que representan la misma cadena de caracteres. El `CString` clase sobrecarga el operador de igualdad (`==`) para comparar dos `CString` objetos basan en su valor (contenido) en lugar de su identidad (dirección).  
  
## <a name="see-also"></a>Vea también  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

