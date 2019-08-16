---
title: Inicialización de OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 6860697dd3adbe26197dd9075e84f402029e00a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502021"
---
# <a name="ole-initialization"></a>Inicialización de OLE

Para que una aplicación pueda utilizar los servicios del sistema OLE, debe inicializar los archivos DLL del sistema OLE y comprobar que los archivos dll tienen la versión correcta. La `AfxOleInit` función inicializa los archivos DLL del sistema OLE.

### <a name="ole-initialization"></a>Inicialización de OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicializa las bibliotecas OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Llame a esta función en la función del `InitInstance` objeto de aplicación para habilitar la compatibilidad con la contención de controles OLE.|

## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

Llame a esta función en la función del `InitInstance` objeto de aplicación para habilitar la compatibilidad con la contención de controles OLE.

### <a name="syntax"></a>Sintaxis

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los controles OLE (ahora denominados controles ActiveX), vea temas de controles [ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="afxoleinit"></a>  AfxOleInit

Inicializa la compatibilidad con OLE para la aplicación.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ejecuta correctamente; 0 si se produce un error en la inicialización, posiblemente porque se han instalado versiones incorrectas de los archivos DLL del sistema OLE.

### <a name="remarks"></a>Comentarios

Llame a esta función para inicializar la compatibilidad con OLE para una aplicación MFC. Cuando se llama a esta función, tienen lugar las acciones siguientes:

- Inicializa la biblioteca COM en el apartamento actual de la aplicación de llamada. Para obtener más información, vea [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Crea un objeto de filtro de mensajes, implementando la interfaz [IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter) . Se puede tener acceso a este filtro de mensajes con una llamada a [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Si se llama a **AfxOleInit** desde un archivo dll de MFC, se producirá un error en la llamada. El error se produce porque la función supone que, si se llama desde un archivo DLL, la aplicación de llamada inicializó previamente el sistema OLE.

> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si llama a [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) en la `InitInstance` invalidación, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
