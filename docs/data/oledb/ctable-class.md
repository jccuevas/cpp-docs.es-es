---
title: CTable (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7dc1383199b5e8167936d99d487bdfc3eb15bddb
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233495"
---
# <a name="ctable-class"></a>CTable (Clase)
Proporciona un medio para tener acceso directamente a un conjunto de filas sencillo (uno sin parámetros).  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
```  
  
### <a name="parameters"></a>Parámetros  
 *TAccessor*  
 Una clase de descriptor de acceso.  
  
 *TRowset*  
 Una clase de conjunto de filas.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Abrir](#open)|Se abre en la tabla.|  
  
## <a name="remarks"></a>Comentarios  
 Consulte [CCommand](../../data/oledb/ccommand-class.md) para obtener información sobre cómo ejecutar un comando para obtener acceso a un conjunto de filas.  

## <a name="open"></a> CTable:: Open
Se abre en la tabla.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Sesión*  
 [in] La sesión para el que se abre en la tabla.  
  
 *wszTableName*  
 [in] El nombre de la tabla para poder abrirlos, se pasa como una cadena Unicode.  
  
 *szTableName*  
 [in] El nombre de la tabla para poder abrirlos, se pasa como una cadena ANSI.  
  
 *dbid*  
 [in] El `DBID` de la tabla que desea abrir.  
  
 *pPropSet*  
 [in] Un puntero a una matriz de [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/library/ms713696.aspx) en el *referencia del programador OLE DB* en el SDK de Windows. El valor predeterminado es null, especifica ninguna propiedad.  
  
 *ulPropSets*  
 [in] El número de [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) pasan las estructuras en el *pPropSet* argumento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
