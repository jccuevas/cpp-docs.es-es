---
title: CArrayRowset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b367fc74fdbb03a6e5193f3fc9be08f74111a09
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207492"
---
# <a name="carrayrowset-class"></a>CArrayRowset (Clase)
Tiene acceso a los elementos de un conjunto de filas mediante la sintaxis de la matriz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
### <a name="parameters"></a>Parámetros  
 *TAccessor*  
 El tipo de clase de descriptor de acceso que desea que las filas que se va a usar.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CArrayRowset](#carrayrowset)|Constructor.|  
|[Instantánea](#snapshot)|Lee el conjunto de filas completo en la memoria.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador&#91;&#93;](#operator)|Tiene acceso a un elemento del conjunto de filas.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](#nrowsread)|El número de filas ya leídas.|  
  
## <a name="carrayrowset"></a> CArrayRowset:: CArrayRowset
Crea un nuevo objeto `CArrayRowset`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      CArrayRowset(int nMax = 100000);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Nmáx.*  
 [in] Número máximo de filas del conjunto de filas. 

## <a name="snapshot"></a> CArrayRowset:: Snapshot
Lee el conjunto de filas completo en memoria, la creación de una imagen o instantánea de él.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Snapshot() throw();  
  
```  

## <a name="operator"></a> CArrayRowset:: operator
Proporciona la sintaxis de matriz para obtener acceso a una fila del conjunto de filas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *TAccessor*  
 Un parámetro de plantilla que especifica el tipo de descriptor de acceso almacenada en el conjunto de filas.  
  
 *funciones nRow*  
 [in] Número de la fila (elemento de matriz) que desea tener acceso.  
  
### <a name="return-value"></a>Valor devuelto  
 El contenido de la fila solicitada.  
  
### <a name="remarks"></a>Comentarios  
 Si *funciones nRow* supera el número de filas del conjunto de filas, se produce una excepción.  

## <a name="nrowsread"></a> CArrayRowset:: M_nrowsread
Contiene el número de filas del conjunto de filas que ya se han leído.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
ULONG m_nRowsRead;  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset (Clase)](../../data/oledb/crowset-class.md)