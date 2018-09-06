---
title: Semántica de CString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 256c71cace15a3906ac048819ab2ffdef2071ff4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761278"
---
# <a name="cstring-semantics"></a>Semántica de CString

Aunque [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos son objetos dinámicos que pueden crecer, actúan como tipos primitivos integrados y clases simples. Cada `CString` objeto representa un valor único. `CString` los objetos deben considerarse como las cadenas reales en lugar de punteros a cadenas.

Puede asignar uno `CString` objeto a otro. Sin embargo, cuando se modifica uno de los dos `CString` objetos, el otro `CString` objeto no se modifica, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Tenga en cuenta en el ejemplo que los dos `CString` objetos se consideran "equal", ya que representan la misma cadena de caracteres. El `CString` clase sobrecarga el operador de igualdad (`==`) para comparar dos `CString` objetos basan en su valor (contenido) en lugar de su identidad (dirección).

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)

