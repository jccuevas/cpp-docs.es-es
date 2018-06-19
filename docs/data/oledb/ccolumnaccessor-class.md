---
title: CColumnAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d211277a8354d94f1892b97ea8f808cc0b22c30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095325"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor (Clase)
Genera el código de consumidor insertado.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>Comentarios  
 En el código insertado, todas las columnas se enlaza como un descriptor de acceso independiente. Debe tener en cuenta que esta clase se utiliza en el código insertado (por ejemplo, pueden surgir, al depurar), pero normalmente nunca es necesario utilizar directamente, ni a sus métodos.  
  
 `CColumnAccessor` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponden en la funcionalidad de otros métodos de la clase de descriptor de acceso:  
  
-   `CColumnAccessor` El constructor; crea e inicializa la `CColumnAccessor` objeto.  
  
-   `CreateAccessor` Asigna memoria a estructuras de enlace de la columna e inicializa a los miembros de datos de columna.  
  
-   **BindColumns** enlaza las columnas a los descriptores de acceso.  
  
-   **SetParameterBuffer** asigna búferes de parámetros.  
  
-   `AddParameter` Agrega una entrada de parámetro a las estructuras de entrada de parámetro.  
  
-   **HasOutputColumns** determina si el descriptor de acceso tiene columnas de salida  
  
-   **HasParameters** determina si el descriptor de acceso tiene parámetros.  
  
-   `BindParameters` Enlaza los parámetros creados a las columnas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)