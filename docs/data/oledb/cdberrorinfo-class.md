---
title: CDBErrorInfo (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ae65a1a04d5befdfcd22327def8f60d96c9d4cff
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo (Clase)
Proporciona compatibilidad para el procesamiento de error de OLE DB mediante OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CDBErrorInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|Devuelve toda la información de error incluida en un registro de error.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Llamadas [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) para devolver información básica sobre el error especificado.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Llamadas [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) para devolver un puntero a una interfaz en un objeto de error personalizado.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Llamadas [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) para devolver un **IErrorInfo** puntero de interfaz para el registro especificado.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Llamadas [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) para devolver los parámetros de error.|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|Obtiene los registros de error para el objeto especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz devuelve uno o más registros de error al usuario. Llame a [cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) primero, que se va a obtener un recuento de registros de error. Llame a uno el acceso a las funciones, como [cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)para recuperar información de error para cada registro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [DBViewer](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)