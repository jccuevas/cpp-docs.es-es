---
title: CEnumeratorAccessor::m_szParseName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
dev_langs:
- C++
helpviewer_keywords:
- m_szParseName
ms.assetid: 32e826b6-0890-4db4-aa92-fc1ea3f528b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5089ff7531c349afc8a8f7991cfcb0ff97c4bd52
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cenumeratoraccessormszparsename"></a>CEnumeratorAccessor::m_szParseName
Cadena que se pasarán a [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) para obtener un moniker para el origen de datos o enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
WCHAR m_szParseName[129];  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Vea [ISourcesRowset:: GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx) en el *referencia del programador de OLE DB* para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CEnumeratorAccessor (Clase)](../../data/oledb/cenumeratoraccessor-class.md)