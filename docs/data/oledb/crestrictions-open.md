---
title: 'CRestrictions:: Open | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8039d55312687cc28be27f2ed7726b9bda1b44aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097437"
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
Devuelve un resultado que se establece de acuerdo con las restricciones proporcionadas por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `session`  
 [in] Especifica un objeto de sesión existente que usa para conectarse al origen de datos.  
  
 *lpszParam*  
 [in] Especifica las restricciones en el conjunto de filas de esquema.  
  
 `bBind`  
 [in] Especifica si se debe enlazar automáticamente la asignación de columna. El valor predeterminado es **true**, lo que hace que el mapa de columnas enlazar automáticamente. Establecer `bBind` a **false** evita que el enlace automático de la asignación de columna para que pueda enlazar manualmente. (Enlace manual es de particular interés para los usuarios OLAP).  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 Puede especificar un máximo de siete restricciones en un conjunto de filas de esquema.  
  
 Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) para obtener información acerca de las restricciones definidas en cada conjunto de filas de esquema.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (clase)](../../data/oledb/crestrictions-class.md)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)