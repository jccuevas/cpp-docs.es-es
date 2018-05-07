---
title: AtlTraceErrorRecords | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afea3c3ef1f169e5f1cb5fc675c74b54da1be0d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
Vuelca la información de registro de Error de OLE DB en el dispositivo de volcado de memoria si se devuelve un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hErr`  
 [in] Un `HRESULT` devuelto por una función de miembro de la plantilla de consumidor OLE DB.  
  
## <a name="remarks"></a>Comentarios  
 Si `hErr` no `S_OK`, `AtlTraceErrorRecords` vuelca la información de registro de Error de OLE DB en el dispositivo de volcado de memoria (el **depurar** ficha de la ventana de salida o un archivo). La información de registro de Error, que se obtiene del proveedor, incluye el número de fila, origen, descripción, archivo de ayuda, contexto y GUID para cada entrada de registro de error. `AtlTraceErrorRecords` Esta información solo en compilaciones de depuración de volcados de memoria. En versiones de lanzamiento, es un código auxiliar vacío que se optimiza out.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo (Clase)](../../data/oledb/cdberrorinfo-class.md)