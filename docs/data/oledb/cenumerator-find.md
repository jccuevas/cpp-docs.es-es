---
title: 'CEnumerator:: Find | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 863832f41c866764883336c7de76fa343eb1cbac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
Busca un nombre especificado entre los proveedores disponibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *szSearchName*  
 [in] El nombre que se buscará.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si se encontró el nombre. en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Este nombre se asigna a la **SOURCES_NAME** miembro de la [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CEnumerator (Clase)](../../data/oledb/cenumerator-class.md)