---
title: CNoRowset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a838bc904a4f09f72962ce7c991bab8e5ac8fcbf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074843"
---
# <a name="cnorowset-class"></a>CNoRowset (Clase)

Se puede usar como un argumento de plantilla (`TRowset`) para [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
### <a name="parameters"></a>Parámetros  

*TAccessor*<br/>
Una clase de descriptor de acceso. De manera predeterminada, es `CAccessorBase`.  
  
## <a name="remarks"></a>Comentarios  

Use `CNoRowset` como argumento de plantilla si el comando no devuelve un conjunto de filas.  
  
`CNoRowset` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de clase de descriptor de acceso:  
  
- `BindFinished` : Indica cuando el enlace está completando (devuelve `S_OK`).  
  
- `Close` -Libera las filas y la interfaz IRowset actual.  
  
- `GetIID` -Recupera el identificador de interfaz de un punto de conexión.  
  
- `GetInterface` -Recupera una interfaz.  
  
- `GetInterfacePtr` -Recupera un puntero de interfaz encapsulado.  
  
- `SetAccessor` -Establece un puntero al descriptor de acceso.  
  
- `SetupOptionalRowsetInterfaces` -Configura interfaces opcionales para el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  

**Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)