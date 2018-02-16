---
title: CNoAccessor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs:
- C++
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9c609a3e15f40311984308c48efbf24d931e188
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cnoaccessor-class"></a>CNoAccessor (Clase)
Puede usarse como un argumento de plantilla (`TAccessor`) para las clases de plantilla como `CCommand` y `CTable`, que requieren un argumento de la clase de descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CNoAccessor  
```  
  
## <a name="remarks"></a>Comentarios  
 Use `CNoAccessor` como un argumento de plantilla cuando no desee que la clase para admitir parámetros o columnas de salida.  
  
 `CNoAccessor` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de la clase de descriptor de acceso:  
  
-   **BindColumns** -enlaza las columnas a los descriptores de acceso.  
  
-   `BindParameters` -Enlaza los parámetros creados a las columnas.  
  
-   **Enlazar** -crea enlaces.  
  
-   **Cerrar** -cierra el descriptor de acceso.  
  
-   `ReleaseAccessors` -Libera los descriptores de acceso creados por la clase.  
  
-   `FreeRecordMemory` -Libera las columnas en el registro actual que deben ser liberados.  
  
-   `GetColumnInfo` -Obtiene información de columna del conjunto de filas abierto.  
  
-   `GetNumAccessors` -Recupera el número de descriptores de acceso creado por la clase.  
  
-   `IsAutoAccessor` -Devuelve true si los datos se recuperan automáticamente para el descriptor de acceso durante una operación de movimiento.  
  
-   `GetHAccessor` -Recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.  
  
-   `GetBuffer` -Recupera el puntero al búfer de marcador.  
  
-   **NoBindOnNullRowset** -impide que el enlace de datos en conjuntos de filas vacío.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)