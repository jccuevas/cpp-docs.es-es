---
title: "Superar las pruebas de conformidad de OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pruebas de conformidad"
  - "pruebas de conformidad [OLE DB]"
  - "proveedores OLE DB, pruebas"
  - "probar proveedores"
  - "pruebas, proveedores OLE DB"
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Superar las pruebas de conformidad de OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para conseguir que los proveedores sean más coherentes, el SDK de Data Access proporciona un conjunto de pruebas de conformidad de OLE DB.  Las pruebas comprueban todos los aspectos del proveedor y proporcionan una garantía razonable de que el proveedor funciona de la manera esperada.  Puede encontrar las pruebas de conformidad con OLE DB en el SDK de Microsoft Data Access.  Esta sección está centrada en lo que hay que hacer para superar las pruebas de conformidad.  Para obtener información sobre la realización de las pruebas de conformidad con OLE DB, vea el SDK.  
  
## Realizar las pruebas de conformidad  
 En Visual C\+\+ 6.0, las plantillas de proveedor OLE DB agregaban varias funciones de enlace para permitir la comprobación de valores y propiedades.  La mayoría de estas funciones se agregaron a causa de las pruebas de conformidad.  
  
> [!NOTE]
>  Debe agregar varias funciones de validación para que el proveedor supere las pruebas de conformidad con OLE DB.  
  
 Este proveedor requiere dos rutinas de validación.  La primera rutina, `CRowsetImpl::ValidateCommandID`, forma parte de la clase de conjunto de filas.  Las plantillas de proveedor llaman a esta rutina durante la creación del conjunto de filas.  El ejemplo utiliza esta rutina para indicar a los consumidores que no admite índices.  La primera llamada se hace a `CRowsetImpl::ValidateCommandID` \(tenga en cuenta que el proveedor utiliza la definición de tipo **\_RowsetBaseClass** agregada en el mapa de interfaz para `CMyProviderRowset` de [Compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md), de forma que no tenga que escribir esa larga línea de argumentos de plantilla\).  A continuación, devuelva **DB\_E\_NOINDEX** si el parámetro de índice no es de tipo **NULL** \(es decir, el consumidor desea utilizar un índice en el proveedor\).  Para obtener más información sobre identificadores de comandos, busque **IOpenRowset::OpenRowset** en las especificaciones de OLE DB.  
  
 El código siguiente es la rutina de validación de **ValidateCommandID**:  
  
```  
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
  
 Las plantillas de proveedor llaman al método `OnPropertyChanged` siempre que alguien cambie el valor de una propiedad del grupo **DBPROPSET\_ROWSET**.  Si desea controlar propiedades de otros grupos, agréguelas al objeto apropiado \(es decir, las comprobaciones de **DBPROPSET\_SESSION** corresponden a la clase `CMyProviderSession`\).  
  
 En primer lugar, el código comprueba si la propiedad está vinculada a otra propiedad.  Si se está encadenando la propiedad, se establece el valor de la propiedad **DBPROP\_BOOKMARKS** en True.  El Apéndice C de la especificación de OLE DB contiene información acerca de las propiedades.  Esta información también le indica si la propiedad está encadenada a otra.  
  
 Puede que también desee agregar al código la rutina `IsValidValue`.  Las plantillas llaman a `IsValidValue` al intentar establecer una propiedad.  Si requiere procesamiento adicional al establecer el valor de una propiedad, debe reemplazar este método.  Puede tener uno de estos métodos para cada conjunto de propiedades.  
  
## Cuestiones de subprocesamiento  
 De manera predeterminada, el Asistente para proveedores OLE DB del Asistente para proveedores OLE DB ATL generará código para que el proveedor se ejecute en un modelo apartamento.  Si intenta ejecutar este código con las pruebas de conformidad, inicialmente se producirán errores.  Esto se debe a que Ltm.exe, la herramienta utilizada para ejecutar las pruebas de conformidad de OLE DB, utiliza de manera predeterminada el subproceso libre.  El código del Asistente para proveedores OLE DB utiliza de manera predeterminada el modelo apartamento para obtener mejor rendimiento y facilitar su uso.  
  
 Para solucionar este problema, puede cambiar LTM o el proveedor.  
  
#### Para cambiar LTM de forma que se ejecute en modo de subproceso de apartamento  
  
1.  En el menú principal de LTM, haga clic en **Herramientas** y, a continuación, en **Opciones**.  
  
2.  En la ficha **General**, cambie el modelo de subprocesos de **Subproceso libre** a **Subproceso de apartamento**.  
  
 Para cambiar el proveedor de forma que se ejecute en modo de subproceso libre:  
  
-   En el proyecto de proveedor, busque todas las instancias de `CComSingleThreadModel` y reemplácelas por `CComMultiThreadModel`, que debe estar en los encabezados de origen de datos, sesión y conjunto de filas.  
  
-   Cambie en el archivo .rgs el modelo de subprocesos de **Apartamento** a **Combinado**.  
  
-   Siga las normas de programación correctas para la programación de subproceso libre \(es decir, bloqueo al escribir\).  
  
## Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)