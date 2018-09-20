---
title: Imprimir mediante programación | Microsoft Docs
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
ms.openlocfilehash: 527ecd89838702a3ec8a91c35e67c1c0cc26501e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397843"
---
# <a name="programmatic-printing"></a>Imprimir mediante programación

OLE proporciona los medios para identificar de forma única documentos persistentes (`GetClassFile`) y cargarlos en su código asociado (`CoCreateInstance`, `QueryInterface(IID_IPersistFile)`, `QueryInterface(IID_IPersistStorage)`, `IPersistFile::Load`, y `IPersistStorage::Load`). Para habilitar la impresión de documentos, la contención de documentos activos (mediante un diseño existente de OLE no se distribuyen con OLE 2.0 originalmente) presenta una interfaz estándar de la base de impresión, `IPrint`, disponible con carácter general a través de cualquier objeto que se puede cargar el estado persistente del tipo de documento. Cada vista de un documento activo, opcionalmente, puede admitir el `IPrint` interfaz para proporcionar estas capacidades.

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

Contenedores y los clientes usan `IPrint::Print` para indicar el documento que se imprima una vez que ese documento se carga, especificar los indicadores de control de impresión, el dispositivo de destino, las páginas que se va a imprimir y opciones adicionales. El cliente también puede controlar la continuación de la impresión a través de la interfaz `IContinueCallback` (ver abajo).

Además, `IPrint::SetInitialPageNum` admite la posibilidad de imprimir una serie de documentos como uno con la numeración de páginas de forma una ventaja para los contenedores de documentos activos como el cuaderno de Office. `IPrint::GetPageInfo` permite mostrar información de paginación sencillo al permitir que el llamador recuperar el inicio de página número anteriormente pasado a `SetInitialPageNum` (o predeterminada interna del documento el número de página de inicio) y el número de páginas del documento.

Los objetos que admiten `IPrint` se marcan en el registro con la clave "Printable" almacenada en el CLSID del objeto:

HKEY_CLASSES_ROOT\CLSID\\{...} \Printable

`IPrint` Normalmente se implementa en el mismo objeto que admite cualquiera `IPersistFile` o `IPersistStorage`. Los autores de llamadas, tenga en cuenta la capacidad de imprimir mediante programación el estado persistente de alguna clase mediante una búsqueda en el registro para la clave "Printable". Actualmente, "Imprimibles" indican compatibilidad con al menos `IPrint`; otras interfaces pueden definirse en el futuro, a continuación, lo que estaría disponible a través de `QueryInterface` donde `IPrint` simplemente representa el nivel de base de soporte técnico.

Durante un procedimiento de impresión, puede que el cliente o el contenedor que inició la impresión para controlar si debe continuar la impresión. Por ejemplo, el contenedor puede admitir un comando "Detener la impresión" que debe finalizar el trabajo de impresión tan pronto como sea posible. Para admitir esta funcionalidad, el cliente de un objeto imprimible puede implementar un objeto de receptor de notificaciones pequeña con la interfaz `IContinueCallback`:

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

Esta interfaz está diseñada para ser útil como una función de devolución de llamada de continuación genérico que ocupa el lugar de los diversos procedimientos de continuación de la API Win32 (como el `AbortProc` para la impresión y la `EnumMetafileProc` para la enumeración de metarchivo). Por lo tanto el diseño de la interfaz es útil en una amplia variedad de procesos que requieren mucho tiempo.

En los casos más genéricos, la `IContinueCallback::FContinue` cualquier proceso largo llama periódicamente a función. El objeto receptor devuelve S_OK para continuar con la operación y S_FALSE para detener el procedimiento tan pronto como sea posible.

`FContinue`, sin embargo, no se utiliza en el contexto de `IPrint::Print`; en su lugar, impresión utiliza `IContinueCallback::FContinuePrint`. Podría llamar periódicamente cualquier objeto de impresión `FContinuePrinting` pasa el número de páginas que han sido imprimir, el número de la página que se va a imprimir y una cadena adicional que describe el estado de impresión que el cliente puede optar por mostrar al usuario (por ejemplo, "página de 5 de 19").

## <a name="see-also"></a>Vea también

[Contenedores de documentos activos](../mfc/active-document-containers.md)

