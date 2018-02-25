---
title: CDynamicStringAccessor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f13eb935cae82b0383e87c90bbe17d35d399fbdb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor (Clase)
Permite obtener acceso a un origen de datos cuando no tiene ningún conocimiento del esquema de base de datos (estructura subyacente de la base de datos).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|Recupera los datos de la columna especificada como una cadena.|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|Establece los datos de la columna especificada como una cadena.|  
  
## <a name="remarks"></a>Comentarios  
 Mientras [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) solicita datos en el formato nativo notificado por el proveedor, `CDynamicStringAccessor` solicita que el proveedor recupere todos los datos que se tiene acceso desde el almacén de datos como datos de cadena. Esto es especialmente útil para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como mostrar o imprimir el contenido del almacén de datos.  
  
 El tipo de datos de columna en el almacén de datos nativo no importa; siempre que el proveedor puede admitir la conversión de datos, proporcionará los datos en formato de cadena. Si el proveedor no admite la conversión de tipo de datos nativo a una cadena (que no es muy común), la llamada solicita devolverá el valor de éxito **DB_S_ERRORSOCCURED**, y el estado de la columna correspondiente indicar un problema de conversión con **DBSTATUS_E_CANTCONVERTVALUE**.  
  
 Use `CDynamicStringAccessor` métodos para obtener información de columna. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución.  
  
 La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener datos desde el búfer mediante [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), ni lo almacena en el búfer mediante [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Para obtener una descripción y ejemplos del uso de las clases de descriptor de acceso dinámico, vea [utilizando descriptores de acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor (clase)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor (clase)](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA (clase)](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW (clase)](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor (Clase)](../../data/oledb/cxmlaccessor-class.md)