---
title: CAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dffefb74faf6836b9f2fc81a7800dc34084657cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="caccessor-class"></a>CAccessor (Clase)
Representa uno de los tipos de descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase de registro de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Se utiliza cuando un registro de forma estática se enlaza a un origen de datos. El registro contiene el búfer. Esta clase admite varios descriptores de acceso en un conjunto de filas.  
  
 Use este tipo de descriptor de acceso si conoce la estructura y el tipo de la base de datos.  
  
 Si el descriptor de acceso contiene campos que apuntan a la memoria (como un `BSTR` o interfaz) que debe ser liberado, llame a la función miembro [CAccessorRowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md) antes de la siguiente se lee el registro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)