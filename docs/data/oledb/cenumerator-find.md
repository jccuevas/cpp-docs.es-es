---
title: 'CEnumerator:: Find | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2466127dab53fa6646a4f149400e4318aed59970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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