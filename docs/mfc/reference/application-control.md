---
title: Control de la aplicación
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612299"
---
# <a name="application-control"></a>Control de la aplicación

OLE requiere un control considerable sobre las aplicaciones y sus objetos. La DLL del sistema OLE debe ser capaz de iniciar y publicar aplicaciones de forma automática, coordinar su producción y la modificación de objetos y así sucesivamente. Las funciones en este tema cumplen esos requisitos. Además de la DLL del sistema OLE que se llama, estas funciones deben llamarse a veces también las aplicaciones.

### <a name="application-control"></a>Control de la aplicación

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Indica si puede finalizar la aplicación.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Recupera el filtro de mensajes de la aplicación actual.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Recupera la marca de control de usuario actual.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Establece o borra la marca de control de usuario.|
|[AfxOleLockApp](#afxolelockapp)|Incrementa el recuento global del marco de trabajo del número de objetos activos en una aplicación.|
|[AfxOleLockControl](#afxolelockcontrol)| Bloquea el generador de clases del control especificado. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Disminuye recuento de .NET framework del número de objetos activos en una aplicación.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Desbloquea el generador de clases del control especificado. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Registra un servidor en el registro del sistema OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementa la interfaz de usuario para el *typename* objeto comando.|

##  <a name="afxolecanexitapp"></a>  AfxOleCanExitApp

Indica si puede finalizar la aplicación.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede salir de la aplicación; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Una aplicación no debe finalizar si hay referencias pendientes en sus objetos. Las funciones globales `AfxOleLockApp` y `AfxOleUnlockApp` incremento y decremento, respectivamente, un contador de referencias a objetos de la aplicación. La aplicación no debería finalizar cuando este contador es distinto de cero. Si el contador es distinto de cero, la ventana principal de la aplicación se oculta (no destruido) cuando el usuario elige cerrar en el menú de sistema o la salida en el menú archivo. El marco de trabajo llama a esta función `CFrameWnd::OnClose`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter

Recupera el filtro de mensajes de la aplicación actual.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Valor devuelto

Un puntero para el filtro de mensajes actual.

### <a name="remarks"></a>Comentarios

Llame a esta función para obtener acceso a la actual `COleMessageFilter`-derivado, tal como se llamaría a `AfxGetApp` para tener acceso al objeto de aplicación actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: afxwin.h

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl

Recupera la marca de control de usuario actual.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario está en el control de la aplicación. en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El usuario está en el control de la aplicación cuando el usuario tiene abierto explícitamente o se crea un nuevo documento. El usuario sea también en el control si la DLL del sistema OLE no inició la aplicación, en otras palabras, si el usuario inicia la aplicación con el shell del sistema.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl

Establece o borra la marca de control de usuario, que se explica en la referencia para `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parámetros

*bUserCtrl*<br/>
Especifica si la marca de control de usuario se va a establecer o borrar.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función cuando el usuario crea o carga un documento, pero no cuando un documento está cargado o creado a través de una acción indirecta, como la carga de un objeto incrustado desde una aplicación contenedora.

Llame a esta función si otras acciones en la aplicación deben poner al usuario en el control de la aplicación.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp

Incrementa el recuento global del marco de trabajo del número de objetos activos de la aplicación.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo mantiene un recuento del número de objetos activos en una aplicación. El `AfxOleLockApp` y `AfxOleUnlockApp` funciones, respectivamente, aumentar y disminuir este número.

Cuando el usuario intenta cerrar una aplicación que tenga objetos activos: una aplicación para que el recuento de objetos activos es distinto de cero, el marco de trabajo oculta la aplicación desde la vista del usuario en lugar de apagarlo completamente. El `AfxOleCanExitApp` función indica si puede finalizar la aplicación.

Llamar a `AfxOleLockApp` desde cualquier objeto que exponga las interfaces OLE, si podría no ser deseable para ese objeto se destruya mientras aún está en uso por una aplicación cliente. También llamar `AfxOleUnlockApp` en el destructor de cualquier objeto que llama a `AfxOleLockApp` en el constructor. De forma predeterminada, `COleDocument` (y las clases derivadas) automáticamente bloquear y desbloquear la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp

Disminuye recuento del marco de trabajo de objetos activos en la aplicación.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Comentarios

Consulte `AfxOleLockApp` para obtener más información.

Cuando el número de objetos activos llega a cero, `AfxOleOnReleaseAllObjects` se llama.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Bloquea el generador de clases del control especificado para que los datos creados dinámicamente asociados al control permanecen en memoria.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase única del control.

*lpszProgID*<br/>
El identificador único del programa del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control ha bloqueado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esto puede acelerar considerablemente la presentación de los controles. Por ejemplo, una vez al crear un control en un cuadro de diálogo y bloquear el control con `AfxOleLockControl`, no es necesario crear y eliminar de nuevo cada vez que se muestra o se destruye el cuadro de diálogo. Si el usuario abre y cierra un cuadro de diálogo varias veces, los controles de bloqueo puede mejorar considerablemente el rendimiento. Cuando esté preparado para destruir el control, llame a `AfxOleUnlockControl`.

### <a name="example"></a>Ejemplo

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass

Esta función permite registrar el servidor en el registro del sistema OLE.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
Referencia al Id. del servidor OLE

*lpszClassName*<br/>
Puntero a una cadena que contiene el nombre de clase de objetos del servidor.

*lpszShortTypeName*<br/>
Puntero a una cadena que contiene el nombre corto del tipo de objeto del servidor, por ejemplo, "Gráfico".

*lpszLongTypeName*<br/>
Puntero a una cadena que contiene el nombre largo del tipo de objeto del servidor, por ejemplo, "Gráfico de Microsoft Excel 5.0".

*nAppType*<br/>
Un valor, tomado de la enumeración OLE_APPTYPE, especifica el tipo de aplicación OLE. Los valores posibles son los siguientes:

- OAT_INPLACE_SERVER Server tiene interfaz de usuario de servidor completo.

- OAT_SERVER Server admite solo la incrustación de objetos.

- OAT_CONTAINER contenedor admite vínculos con incrustaciones.

- OAT_DISPATCH_OBJECT `IDispatch`-objeto capaz.

*rglpszRegister*<br/>
Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE si no se encuentra ningún valor existente para las claves.

*rglpszOverwrite*<br/>
Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE, si el registro contiene los valores existentes de las claves especificadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la clase de servidor se ha registrado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Puede usar la mayoría de las aplicaciones `COleTemplateServer::Register` para registrar los tipos de documento de la aplicación. Si el formato de registro del sistema de la aplicación no ajusta el patrón típico, puede usar `AfxOleRegisterServerClass` para un mayor control.

El registro consta de un conjunto de claves y valores. El *rglpszRegister* y *rglpszOverwrite* argumentos son matrices de punteros a cadenas, que consta de una clave y valor separan por un **NULL** carácter ( `'\0'`). Cada una de estas cadenas puede tener parámetros reemplazables marcados por las secuencias de caracteres cuyas posiciones *%1* a través de *%5*.

Los símbolos se rellenan como sigue:

|Símbolo|Valor|
|------------|-----------|
|%1|Id. de clase, con formato de cadena|
|%2|Nombre de la clase|
|%3|Ruta de acceso al archivo ejecutable|
|%4|Nombre de tipo corto|
|%5|Nombre de tipo Long|

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu

Implementa la interfaz de usuario para el *typename* objeto comando.

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>Parámetros

*pClient*<br/>
Un puntero al elemento de cliente OLE.

*pMenu*<br/>
Un puntero al objeto de menú para actualizarse.

*iMenuItem*<br/>
El índice del elemento de menú para actualizarse.

*nIDVerbMin*<br/>
El identificador de comando que se corresponde con el verbo principal.

*nIDVerbMax*<br/>
El identificador de comando que corresponde al último verbo.

*nIDConvert*<br/>
Id. del elemento de menú de Convert.

### <a name="remarks"></a>Comentarios

Si el servidor reconoce solo un verbo principal, se convierte en el elemento de menú "verbo *typename* objeto" y el *nIDVerbMin* comando se envía cuando el usuario elige el comando. Si el servidor reconoce varios verbos, a continuación, se convierte en el elemento de menú " *typename* objeto" y un submenú que enumera todos los verbos aparece cuando el usuario elige el comando. Cuando el usuario elige un verbo en el submenú, *nIDVerbMin* se envía si se elige el primer verbo, *nIDVerbMin* + 1 se envía si el segundo verbo es elegida y así sucesivamente. El valor predeterminado `COleDocument` esta característica controla automáticamente la implementación.

Debe tener la siguiente instrucción en el script de recursos de aplicación de su cliente (. Archivo RC):

**#include \<afxolecl.rc >**

### <a name="requirements"></a>Requisitos

**Encabezado**: afxole.h

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

Desbloquea el generador de clases del control especificado.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase única del control.

*lpszProgID*<br/>
El identificador único del programa del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control se desbloqueó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Un control esté bloqueado con `AfxOleLockControl`, de modo que los datos creados dinámicamente asociados al control permanecen en memoria. Esto puede aumentar significativamente la velocidad del control porque no se necesita crear y destruir cada vez que se muestra el control. Cuando esté preparado para destruir el control, llame a `AfxOleUnlockControl`.

### <a name="example"></a>Ejemplo

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
