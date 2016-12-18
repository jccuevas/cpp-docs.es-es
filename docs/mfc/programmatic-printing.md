---
title: "Imprimir mediante programaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "documentos activos [C++], imprimir"
  - "IPrint (interfaz)"
  - "imprimir [MFC]"
  - "imprimir [MFC], documentos activos"
  - "imprimir [MFC], mediante programación"
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Imprimir mediante programaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE proporcionaba significa identificar los documentos persistentes \(**GetClassFile**\) y cargarlos en el código asociado \(`CoCreateInstance`, **QueryInterface\(IID\_IPersistFile\)**, **QueryInterface\(IID\_IPersistStorage\)**, **IPersistFile::Load**, y **IPersistStorage::Load**\).  Para habilitar aún más documentos de impresión, contención de documento activo \(mediante un diseño OLE existente no enviado con OLE 2,0 originalmente\) presenta una interfaz de impresión de la base\- estándar, `IPrint`, normalmente \- disponibles a través de cualquier objeto que pueda cargar el estado persistente de tipo de documento.  Cada vista de un documento activo puede admitir opcionalmente a la interfaz de **IPrint** que proporciona estas funciones.  
  
 La interfaz se define de `IPrint` como sigue:  
  
 `interface IPrint : IUnknown`  
  
 `{`  
  
 `HRESULT SetInitialPageNum([in] LONG nFirstPage);`  
  
 `HRESULT GetPageInfo(`  
  
 `[out] LONG *pnFirstPage,`  
  
 `[out] LONG *pcPages);`  
  
 `HRESULT Print(`  
  
 `[in] DWORD grfFlags,`  
  
 `[in,out] DVTARGETDEVICE **pptd,`  
  
 `[in,out] PAGESET ** ppPageSet,`  
  
 `[in,out] STGMEDIUM **ppstgmOptions,`  
  
 `[in] IContinueCallback* pCallback,`  
  
 `[in] LONG nFirstPage,`  
  
 `[out] LONG *pcPagesPrinted,`  
  
 `[out] LONG *pnPageLast);`  
  
 `};`  
  
 El uso **IPrint::Print** customers y los contenedores de simplemente indicar al documento para imprimirse que el documento cargado, especificando el control de impresión marca una vez, el dispositivo de destino, las páginas para imprimir, y opciones adicionales.  El cliente también puede controlar la continuación de impresión a través de la interfaz `IContinueCallback` \(vea a continuación\).  
  
 Además, **IPrint::SetInitialPageNum** admite la capacidad de imprimir una serie de documentos como uno numerando páginas sin problemas, obviamente un marcado para los contenedores del documento activo como el Office binder.  **IPrint::GetPageInfo** crea mostrando información de paginación simple permite que el llamador recupere el número de página inicial último previamente a **SetInitialPageNum** \(o el número de página inicial predeterminado interno de documento\) y el número de páginas en el documento.  
  
 Los objetos que `IPrint` admiten está marcada en el registro con la tecla “Printable” almacenado bajo el CLSID del objeto:  
  
 HKEY\_CLASSES\_ROOT\\CLSID\\{...}\\Printable  
  
 `IPrint` se suele implementar en el mismo objeto que admite `IPersistFile` o `IPersistStorage`.  Los llamadores tienen la capacidad mediante programación de imprimir el estado persistente de alguna clase buscando en el registro de la tecla “Printable”.  Actualmente, “Printable” indica al menos `IPrint`admiten; otras interfaces pueden ser definidas en el futuro que a continuación estará disponible con `QueryInterface` donde **IPrint** representa simplemente el nivel base de compatibilidad.  
  
 Durante un procedimiento de impresión, puede que el cliente o el contenedor que iniciaron la impresión para controlar si la impresión debe continuar.  Por ejemplo, el contenedor puede admitir “un comando de paro de impresión” que debe finalizar el trabajo de impresión lo más rápidamente posible.  Para admitir esta funcionalidad, el cliente de un objeto imprimible puede implementar un objeto de receptor de notificación con la interfaz `IContinueCallback`:  
  
 `interface IContinueCallback : IUnknown`  
  
 `{`  
  
 `HRESULT FContinue(void);`  
  
 `HRESULT FContinuePrinting(`  
  
 `[in] LONG cPagesPrinted,`  
  
 `[in] LONG nCurrentPage,`  
  
 `[in] LPOLESTR pszPrintStatus);`  
  
 `};`  
  
 Esta interfaz está diseñada para ser útil como función de devolución de llamada genérica de continuación que toma el lugar de los distintos procedimientos de continuación de la API Win32 \(como **AbortProc** para imprimir y **EnumMetafileProc** para la enumeración de metarchivo\).  Así este diseño de interfaz es útil en una gran variedad de procesos largos.  
  
 En los casos más genéricos, la función de **IContinueCallback::FContinue** llama periódicamente por cualquier proceso largo.  El objeto de receptor devuelve `S_OK` para continuar la operación, y **S\_FALSE** para detener el procedimiento lo más rápidamente posible.  
  
 **FContinue**, sin embargo, no se utiliza en el contexto de **IPrint::Print**; en su lugar, imprimir utiliza **IContinueCallback::FContinuePrint**.  Cualquier objeto de impresión debe llamar periódicamente **FContinuePrinting** que pasa el número de páginas que han estado imprimir, el número de la página que está impresa, y una cadena adicional que describe el estado de impresión que el cliente puede elegir para mostrar al usuario \(como “página 5 de 19 "\).  
  
## Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)