---
title: CCommand (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 667e86c173a7001ae22036cb1f0dd8f3fbfcf6a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ccommand-class"></a>CCommand (Clase)
Proporciona métodos para establecer y ejecutar un comando.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor,  
          template <typename T> class TRowset = CRowset,  
          class TMultiple = CNoMultipleResults>  
class CCommand :   
           public CAccessorRowset <TAccessor, TRowset>,  
           public CCommandBase,  
           public TMultiple  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 El tipo de clase de descriptor de acceso (como `CDynamicParameterAccessor`, `CDynamicStringAccessor`, o `CEnumeratorAccessor`) que desea que el comando que se utilizará. El valor predeterminado es `CNoAccessor`, que especifica que la clase no admite parámetros o columnas de salida.  
  
 `TRowset`  
 El tipo de clase de conjunto de filas (como `CArrayRowset` o `CNoRowset`) que desea que el comando que se utilizará. De manera predeterminada, es `CRowset`.  
  
 `TMultiple`  
 Para usar un comando de OLE DB que puede devolver varios resultados, especifique [CMultipleResults](../../data/oledb/cmultipleresults-class.md). De lo contrario, utilice [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Para obtener más información, consulte [IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx).  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Cerrar](../../data/oledb/ccommand-close.md)|Cierra el comando actual.|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|Captura el resultado siguiente al utilizar conjuntos de resultados múltiples.|  
|[Abrir](../../data/oledb/ccommand-open.md)|Se ejecuta y, opcionalmente, enlaza el comando.|  
  
### <a name="inherited-methods"></a>Métodos heredados  
  
|||  
|-|-|  
|[Crear](../../data/oledb/ccommand-create.md)|Crea un nuevo comando para la sesión especificada, a continuación, Establece el texto del comando.|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|Crea un nuevo comando.|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|Obtiene una lista de parámetros del comando, sus nombres y sus tipos.|  
|[Preparar](../../data/oledb/ccommand-prepare.md)|Valida y optimiza el comando actual.|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|Libera el descriptor de acceso de parámetro si es necesario, a continuación, libera el comando.|  
|[SetParameterInfo.](../../data/oledb/ccommand-setparameterinfo.md)|Especifica el tipo nativo de cada parámetro de comando.|  
|[Cancelación de preparación](../../data/oledb/ccommand-unprepare.md)|Descarta el plan de ejecución del comando actual.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta clase cuando necesite realizar una operación basada en parámetros o ejecutar un comando. Si simplemente tiene que abrir un conjunto de filas simple, use [CTable](../../data/oledb/ctable-class.md) en su lugar.  
  
 La clase de descriptor de acceso que se usa determina el método de enlace de parámetros y datos.  
  
 Tenga en cuenta que no puede usar los procedimientos almacenados con el proveedor OLE DB para Jet porque ese proveedor no admite almacena procedimientos (sólo se permiten constantes en cadenas de consulta).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)