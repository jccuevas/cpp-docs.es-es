---
title: Inicialización de OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373035"
---
# <a name="ole-initialization"></a>Inicialización de OLE

Antes de que una aplicación pueda usar los servicios del sistema OLE, debe inicializar los archivos DLL del sistema OLE y comprobar que los archivos DLL son la versión correcta. La `AfxOleInit` función inicializa los archivos DLL del sistema OLE.

### <a name="ole-initialization"></a>Inicialización de OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializa las bibliotecas OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Llame a esta función `InitInstance` en la función del objeto de aplicación para habilitar la compatibilidad con la contención de controles OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

Llame a esta función `InitInstance` en la función del objeto de aplicación para habilitar la compatibilidad con la contención de controles OLE.

### <a name="syntax"></a>Sintaxis

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los controles OLE (ahora denominados controles ActiveX), vea Temas de [control ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit

Inicializa la compatibilidad con OLE para la aplicación.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ejecuta correctamente; 0 si se produce un error en la inicialización, posiblemente porque se han instalado versiones incorrectas de los archivos DLL del sistema OLE.

### <a name="remarks"></a>Observaciones

Llame a esta función para inicializar la compatibilidad con OLE para una aplicación MFC. Cuando se llama a esta función, tienen lugar las acciones siguientes:

- Inicializa la biblioteca COM en el apartamento actual de la aplicación de llamada. Para obtener más información, consulte [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Crea un objeto de filtro de mensajes, implementando la interfaz [IMessageFilter.](/windows/win32/api/objidl/nn-objidl-imessagefilter) Se puede tener acceso a este filtro de mensajes con una llamada a [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Si a **AfxOleInit** se llama desde un archivo DLL de MFC, se producirá un error en la llamada. El error se produce porque la función supone que, si se llama desde un archivo DLL, la aplicación de llamada inicializó previamente el sistema OLE.

> [!NOTE]
> Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si llama a [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) en la invalidación, `InitInstance` especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
