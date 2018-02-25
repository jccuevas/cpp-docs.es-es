---
title: AtlTraceErrorRecords | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 024a4331b71b3414aa7d83f27ecaca4e5d2f11de
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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