---
title: Imprimir mediante programación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a439080cec7f3ae96014e9df6ddc65782686bf0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352840"
---
# <a name="programmatic-printing"></a>Imprimir mediante programación
OLE proporciona los medios para identificar de forma única documentos persistentes (**GetClassFile**) y cargarlos en su código asociado (`CoCreateInstance`, **QueryInterface**, **Iid_ipersiststorage**, **IPersistFile:: Load**, y **IPersistStorage:: Load**). Para habilitar la impresión de documentos, la contención de documentos activos (mediante un diseño existente de OLE no incluido con OLE 2.0 originalmente) presenta una interfaz de impresión estándar básica, `IPrint`, que normalmente está disponible a través de cualquier objeto que se puede cargar el estado persistente del tipo de documento. Cada vista de un documento activo, opcionalmente, puede admitir el **IPrint** interfaz para proporcionar estas capacidades.  
  
 El `IPrint` interfaz se define como sigue:  
  
```  
interface IPrint : IUnknown  
    {  
    HRESULT SetInitialPageNum([in] LONG nFirstPage);  
    HRESULT GetPageInfo(  
        [out] LONG *pnFirstPage,  
        [out] LONG *pcPages);  
    HRESULT Print(  
        [in] DWORD grfFlags,  
        [in,out] DVTARGETDEVICE **pptd,  
        [in,out] PAGESET ** ppPageSet,  
        [in,out] STGMEDIUM **ppstgmOptions,  
        [in] IContinueCallback* pCallback,  
        [in] LONG nFirstPage,  
        [out] LONG *pcPagesPrinted,  
        [out] LONG *pnPageLast);  
    };  
```  
  
 Los clientes y los contenedores usan **IPrint:: Print** para indicar el documento que se imprima una vez que se carga el documento, especificar indicadores de control de impresión, el dispositivo de destino, las páginas que se va a imprimir y opciones adicionales. El cliente también puede controlar la continuación de la impresión a través de la interfaz de `IContinueCallback` (ver abajo).  
  
 Además, **IPrint** admite la posibilidad de imprimir una serie de documentos como una numeración de páginas sin problemas, obviamente una ventaja para los contenedores de documentos activos como cuaderno de Office. **IPrint:: GetPageInfo** hace mostrar información de paginación simple al permitir que el autor de la llamada recuperar el inicio página número anteriormente pasado a **SetInitialPageNum** (o valor interno predeterminado del documento número de página inicial) y el número de páginas del documento.  
  
 Objetos que admiten `IPrint` se marcan en el registro con la clave "Printable" almacenada bajo el CLSID del objeto:  
  
 HKEY_CLASSES_ROOT\CLSID\\{...} \Printable  
  
 `IPrint` Normalmente se implementa en el mismo objeto que es compatible con `IPersistFile` o `IPersistStorage`. Los autores de llamadas tenga en cuenta la capacidad de imprimir mediante programación el estado persistente de alguna clase buscando en el registro para la clave "Printable". Actualmente, "Imprimibles" indican compatibilidad con al menos `IPrint`; otras interfaces pueden definirse en el futuro, a continuación, lo que estaría disponible a través de `QueryInterface` donde **IPrint** simplemente representa el nivel de base de soporte técnico.  
  
 Durante un procedimiento de impresión, puede que desee el cliente o el contenedor que inició la impresión para controlar si debe continuar la impresión. Por ejemplo, el contenedor puede admitir un comando "Detener impresión" que debe finalizar el trabajo de impresión tan pronto como sea posible. Para admitir esta capacidad, el cliente de un objeto imprimible puede implementar un objeto de receptor de notificaciones breves con la interfaz de `IContinueCallback`:  
  
```  
interface IContinueCallback : IUnknown  
    {  
    HRESULT FContinue(void);  
    HRESULT FContinuePrinting(  
        [in] LONG cPagesPrinted,  
        [in] LONG nCurrentPage,  
        [in] LPOLESTR pszPrintStatus);  
    };  
```  
  
 Esta interfaz está diseñada para ser útil como una función de devolución de llamada de continuación genérica que ocupa el lugar de los distintos procedimientos de continuación de la API Win32 (como el **AbortProc** para la impresión y la  **EnumMetafileProc** para la enumeración de metarchivo). Por lo tanto, este diseño de la interfaz es útil en una amplia variedad de procesos que consumen muchos recursos.  
  
 En los casos más genéricos, la **IContinueCallback:: FContinue** cualquier proceso largo llama periódicamente a función. Devuelve el objeto receptor `S_OK` para continuar con la operación, y **S_FALSE** para detener el procedimiento tan pronto como sea posible.  
  
 **FContinue**, sin embargo, no se utiliza en el contexto de **IPrint:: Print**; en su lugar, impresión utiliza **IContinueCallback:: FContinuePrint**. Cualquier objeto de impresión debe llamar periódicamente **FContinuePrinting** pasar el número de páginas que han sido imprimir, el número de la página que se va a imprimir y una cadena adicional que describe el estado de impresión que el cliente puede Elija esta opción Mostrar al usuario (por ejemplo, "página 5 de 19").  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)

