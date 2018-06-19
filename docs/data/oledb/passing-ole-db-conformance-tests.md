---
title: Pasar las pruebas de conformidad de OLE DB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11677e6295956de768c7ebc0c113d775b066bb0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110469"
---
# <a name="passing-ole-db-conformance-tests"></a>Superar las pruebas de conformidad de OLE DB
Para que los proveedores de forma que sea más homogénea, el SDK de Data Access proporciona un conjunto de pruebas de conformidad de OLE DB. Las pruebas comprueban todos los aspectos de su proveedor y proporcionan una garantía razonable que el proveedor funciona como se esperaba. Puede encontrar las pruebas de conformidad de OLE DB en el SDK de Microsoft Data Access. En esta sección se centra en lo que se debe hacer para pasar las pruebas de conformidad. Para obtener información acerca de cómo ejecutar las pruebas de conformidad de OLE DB, vea el SDK.  
  
## <a name="running-the-conformance-tests"></a>Ejecuta las pruebas de conformidad  
 En Visual C++ 6.0, las plantillas de proveedor OLE DB agregan una serie de funciones de enlace para que pueda comprobar valores y propiedades. La mayoría de estas funciones se agregaron en respuesta a las pruebas de conformidad.  
  
> [!NOTE]
>  Debe agregar varias funciones de validación para el proveedor pasar las pruebas de conformidad de OLE DB.  
  
 Este proveedor requiere dos rutinas de validación. La primera rutina, `CRowsetImpl::ValidateCommandID`, forma parte de la clase de conjunto de filas. Se llama durante la creación del conjunto de filas mediante las plantillas del proveedor. El ejemplo utiliza esta rutina para indicar a los consumidores que no admite índices. Es la primera llamada `CRowsetImpl::ValidateCommandID` (tenga en cuenta que el proveedor utiliza la **_RowsetBaseClass** typedef agregada en el mapa de interfaz para `CMyProviderRowset` en [compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md), por lo que no es necesario escribir esa larga línea de argumentos de plantilla). A continuación, devolver **DB_E_NOINDEX** si el parámetro de índice no es **NULL** (Esto indica el consumidor desea utilizar un índice en). Para obtener más información sobre identificadores de comando, vea la especificación de OLE DB y busque **IOpenRowset:: OpenRowset**.  
  
 El código siguiente es el **ValidateCommandID** rutina de validación:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)  
{  
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);  
   if (hr != S_OK)  
      return hr;  
  
   if (pIndexID != NULL)  
      return DB_E_NOINDEX;    // Doesn't support indexes  
  
   return S_OK;  
}  
```  
  
 La llamada de plantillas de proveedor la `OnPropertyChanged` método cada vez que alguien cambie una propiedad en el **DBPROPSET_ROWSET** grupo. Si desea controlar propiedades de otros grupos, se agrega al objeto apropiado (es decir, **DBPROPSET_SESSION** comprobaciones de la `CMyProviderSession` clase).  
  
 El código comprueba primero si la propiedad está vinculada a otra. Si se está encadenando la propiedad, Establece la **DBPROP_BOOKMARKS** propiedad en True. Apéndice C de la especificación de OLE DB contiene información acerca de las propiedades. Esta información también indica si la propiedad está encadenada a otra.  
  
 También puede agregar el `IsValidValue` rutinarias en el código. La llamada de plantillas `IsValidValue` al intentar establecer una propiedad. Debe reemplazar este método si requieren un procesamiento adicional cuando se establece un valor de propiedad. Puede tener uno de estos métodos para cada conjunto de propiedades.  
  
## <a name="threading-issues"></a>Problemas con el subprocesamiento  
 De forma predeterminada, el proveedor de Asistente para OLE DB en el Asistente para proveedores OLE DB ATL genera código para el proveedor se ejecute en un modelo de apartamento. Si intenta ejecutar este código con las pruebas de conformidad, inicialmente se producen errores. Esto es porque el valor predeterminado es Ltm.exe, la herramienta utilizada para ejecutar las pruebas de conformidad de OLE DB, para liberar un subproceso. El código de Asistente para proveedores OLE DB tiene como valor predeterminado para el modelo de apartamento de rendimiento y facilidad de uso.  
  
 Para corregir este problema, puede cambiar LTM o cambiar el proveedor.  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>Para cambiar LTM para ejecutarse en el apartamento de subproceso modo  
  
1.  En el menú principal de LTM, haga clic en **herramientas**y, a continuación, haga clic en **opciones**.  
  
2.  En el **General** , modifique el modelo de subprocesamiento de **subproceso libre** a **Apartment Threaded**.  
  
 Para cambiar el proveedor se ejecute en modo de subprocesamiento libre:  
  
-   En el proyecto de proveedor, busque todas las instancias de `CComSingleThreadModel` y sustituirlo por `CComMultiThreadModel`, que debe estar en los encabezados de origen, la sesión y el conjunto de filas de datos.  
  
-   En el archivo .rgs, cambie el modelo de subprocesamiento de **apartamento** a **ambos**.  
  
-   Programación multiproceso de forma gratuita (es decir, el bloqueo en las escrituras) de reglas de programación correcto de seguimiento.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)