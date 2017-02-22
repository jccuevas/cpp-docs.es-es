---
title: "Documentos activos | Microsoft Docs"
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
  - "documentos activos [C++]"
  - "documentos activos [C++], requisitos"
  - "documentos activos [C++], vistas"
  - "OLE [C++], documentos activos"
  - "objetos de vista, requisitos"
  - "vistas [C++], documentos activos"
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Documentos activos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los documentos activos amplían la tecnología de documento compuesto de OLE.  Estas extensiones se proporcionan en forma de interfaces adicionales que administran las vistas, de modo que los objetos puedan funcionar dentro de los contenedores pero mantener el control sobre la presentación y impresión funciona.  Este proceso permite mostrar documentos en marcos no nativos \(como Microsoft Office binder o Microsoft Internet Explorer\) y en marcos nativos \(como propios puertos de la vista del producto\).  
  
 Esta sección describe [requisitos para los documentos activos](#requirements_for_active_documents)funcional.  El documento activos posee un conjunto de datos y tiene acceso al almacenamiento donde los datos se pueden guardar y recuperar.  Puede crear y administrar una o más vistas de sus datos.  Además de admitir la incrustación e interfaces habituales de activación in situ documentos de OLE, el documento activo comunica la posibilidad de crear vistas con `IOleDocument`.  A través de esta interfaz, el contenedor puede pedir crear \(y enumerar posiblemente\) vistas que el documento activo puede mostrar.  A través de esta interfaz, el documento activo también puede proporcionar información diferente sobre sí mismo, por ejemplo si admite varias vistas o rectángulos complejos.  
  
 A continuación se muestra la interfaz de **IOleDocument** .  Observe que la interfaz de **IEnumOleDocumentViews** es un enumerador estándar OLE para los tipos de **IOleDocumentView \*** .  
  
 `interface IOleDocument : IUnknown`  
  
 `{`  
  
 `HRESULT CreateView(`  
  
 `[in] IOleInPlaceSite *pIPSite,`  
  
 `[in] IStream *pstm,`  
  
 `[in] DWORD dwReserved,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);`  
  
 `HRESULT EnumViews(`  
  
 `[out] IEnumOleDocumentViews **ppEnum,`  
  
 `[out] IOleDocumentView **ppView);`  
  
 `}`  
  
 Cada documento activo debe tener un proveedor de cuadro de vista con esta interfaz.  Si el documento no se incrusta dentro de un contenedor, el propio servidor de documentos activos debe proporcionar un cuadro de vista.  Sin embargo, cuando el documento activo se incrusta en un contenedor de documento activo, el contenedor proporciona el cuadro de la vista.  
  
 Un documento activo puede crear uno o más tipos de [vistas](#requirements_for_view_objects) de los datos \(por ejemplo, normal, contorno, diseño de página, etc.\).  Ver actúan como filtros a través de los que los datos pueden considerarse.  Aunque el documento tiene sólo un tipo de vista, todavía puede admitir varias vistas como medio para admitir la funcionalidad de la nueva ventana \(por ejemplo, el elemento de **Nueva ventana** en el menú de **Ventana** en aplicaciones de Office\).  
  
##  <a name="requirements_for_active_documents"></a> Requisitos para los documentos activos  
 Un documento activo que se puede mostrar en un contenedor de documento activo debe:  
  
-   Utilice archivos compuestos OLE como el mecanismo de almacenamiento implementando `IPersistStorage`.  
  
-   Admite las características principales de incrustación de documentos OLE, incluidos **Crear desde archivo**.  Esto necesita las interfaces `IPersistFile`, `IOleObject`, y `IDataObject`.  
  
-   Admite una o más vistas, que es capaz de activación en contexto.  Es decir, las vistas deben admitir la interfaz `IOleDocumentView` así como las interfaces `IOleInPlaceObject` y `IOleInPlaceActiveObject` \(mediante **IOleInPlaceSite** de contenedor y las interfaces de **IOleInPlaceFrame** \).  
  
-   Admite las interfaces `IOleDocument`, `IOleCommandTarget`, y `IPrint`de documentos activos del estándar.  
  
 Conocimiento de cuándo y cómo utilizar las interfaces del contenedor\- lado se implica en estos requisitos.  
  
##  <a name="requirements_for_view_objects"></a> Requisitos para los objetos de vista  
 Un documento activo puede crear una o más vistas de sus datos.  Funcionalmente, estas vistas son los puertos sobre un método set para mostrar los datos.  Si un documento activo sólo admite una vista única, el documento activo y esa vista única se pueden implementar mediante una sola clase.  **IOleDocument::CreateView** devuelve el puntero de interfaz de `IOleDocumentView` del mismo objeto.  
  
 Para trazar dentro de un contenedor de documento activo, un componente de la vista debe admitir **IOleInPlaceObject** y **IOleInPlaceActiveObject** además de `IOleDocumentView`:  
  
 `interface IOleDocumentView : IUnknown`  
  
 `{`  
  
 `HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);`  
  
 `HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);`  
  
 `HRESULT GetDocument([out] IUnknown **ppunk);`  
  
 `[input_sync] HRESULT SetRect([in] LPRECT prcView);`  
  
 `HRESULT GetRect([in] LPRECT prcView);`  
  
 `[input_sync] HRESULT SetRectComplex(`  
  
 `[in] LPRECT prcView,`  
  
 `[in] LPRECT prcHScroll,`  
  
 `[in] LPRECT prcVScroll,`  
  
 `[in] LPRECT prcSizeBox);`  
  
 `HRESULT Show([in] BOOL fShow);`  
  
 `HRESULT UIActivate([in] BOOL fUIActivate);`  
  
 `HRESULT Open(void);`  
  
 `HRESULT CloseView([in] DWORD dwReserved);`  
  
 `HRESULT SaveViewState([in] IStream *pstm);`  
  
 `HRESULT ApplyViewState([in] IStream *pstm);`  
  
 `HRESULT Clone(`  
  
 `[in] IOleInPlaceSite *pIPSiteNew,`  
  
 `[out] IOleDocumentView **ppViewNew);`  
  
 `}`  
  
 Cada vista tiene un sitio asociado de la vista, que encapsula el cuadro y el puerto de vista \(HWND y un área rectangular de esa ventana\).  El sitio expone esta funcionalidad sin embargo la interfaz estándar de **IOleInPlaceSite** .  Tenga en cuenta que es posible tener más de un puerto de un único HWND.  
  
 Normalmente, cada tipo de vista tiene una representación diferente impresa.  Por consiguiente vistas y sitios correspondientes de la vista deben implementar las interfaces de impresión si `IPrint` y `IContinueCallback`, respectivamente.  El cuadro de la vista debe sopesar con el proveedor de la vista con **IPrint** al imprimir comienza, para imprimir encabezados, pies de página, los márgenes, y elementos relacionados correctamente.  El proveedor de vista notifica al cuadro de eventos impresión\- relacionados con `IContinueCallback`.  Para obtener más información sobre el uso de estas interfaces, vea [Imprimir mediante programación](../mfc/programmatic-printing.md).  
  
 Tenga en cuenta que si un documento activo sólo admite una vista única, el documento activo y esa vista única se pueden implementar mediante una clase concreta única.  **IOleDocument::CreateView** simplemente devuelve el puntero de interfaz de `IOleDocumentView` del mismo objeto.  En resumen, no es necesario que haya dos instancias de objeto independientes cuando sólo se necesita una vista.  
  
 Un objeto de vista también puede ser un destino del comando.  Implementar `IOleCommandTarget` una vista puede recibir los comandos que se originan en la interfaz de usuario del contenedor \(como **new**, **Abierta**, **Guardar como**, **Impresión** en el menú de **archivo** ; y **copiar**, **Pegar**, **Deshacer** en el menú de **edición** \).  Para obtener más información, vea [Control de mensajes y destinos de comando](../mfc/message-handling-and-command-targets.md).  
  
## Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)