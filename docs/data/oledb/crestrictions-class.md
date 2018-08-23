---
title: CRestrictions (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b9dc35df928d53d7d5ca5d833db8e87c96e1c7f4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571627"
---
# <a name="crestrictions-class"></a>CRestrictions (Clase)
Una clase genérica que le permite especificar restricciones para los conjuntos de filas de esquema.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
   public CSchemaRowset <T, nRestrictions>  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase utilizada para el descriptor de acceso.  
  
 *nRestrictions*  
 El número de columnas de restricción para el conjunto de filas de esquema.  
  
 *pguid*  
 Un puntero al GUID para el esquema.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h 
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Abrir](#open)|Devuelve un resultado que se establece de acuerdo con las restricciones proporcionadas por el usuario.|   

## <a name="open"></a> CRestrictions:: Open
Devuelve un resultado que se establece de acuerdo con las restricciones proporcionadas por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
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
 *Sesión*  
 [in] Especifica un objeto de sesión existente utilizado para conectarse al origen de datos.  
  
 *lpszParam*  
 [in] Especifica las restricciones en el conjunto de filas de esquema.  
  
 *bBind*  
 [in] Especifica si se debe enlazar automáticamente el mapa de columnas. El valor predeterminado es **true**, lo que hace que el mapa de columnas que se enlazará automáticamente. Establecer *bBind* a **false** impide que el enlace automático de la asignación de columna para que pueda enlazar manualmente. (Enlace manual es de especial interés para los usuarios OLAP).  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Puede especificar un máximo de siete restricciones en un conjunto de filas de esquema.  
  
 Consulte [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) para obtener información sobre las restricciones definidas en cada conjunto de filas de esquema.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)    
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)