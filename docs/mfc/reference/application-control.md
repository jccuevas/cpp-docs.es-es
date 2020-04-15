---
title: Control de la aplicación
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363557"
---
# <a name="application-control"></a>Control de la aplicación

OLE requiere un control sustancial sobre las aplicaciones y sus objetos. Los archivos DLL del sistema OLE deben poder iniciar y liberar aplicaciones automáticamente, coordinar su producción y modificación de objetos, etc. Las funciones de este tema cumplen esos requisitos. Además de ser llamado por los archivos DLL del sistema OLE, a veces estas funciones también deben llamar las aplicaciones.

### <a name="application-control"></a>Control de la aplicación

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Indica si la aplicación puede finalizar.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Recupera el filtro de mensajes actual de la aplicación.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Recupera el indicador de control de usuario actual.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Establece o borra el indicador de control de usuario.|
|[AfxOleLockApp](#afxolelockapp)|Incrementa el recuento global del marco de trabajo del número de objetos activos en una aplicación.|
|[AfxOleLockControl](#afxolelockcontrol)| Bloquea el generador de clases del control especificado. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Disminuye el recuento del marco de trabajo del número de objetos activos en una aplicación.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Desbloquea el generador de clases del control especificado. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Registra un servidor en el registro del sistema OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementa la interfaz de usuario para el comando *typename* Object.|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp

Indica si la aplicación puede finalizar.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la aplicación puede salir; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una aplicación no debe terminar si hay referencias pendientes a sus objetos. Las funciones globales `AfxOleLockApp` y `AfxOleUnlockApp` el incremento y decremento, respectivamente, un contador de referencias a los objetos de la aplicación. La aplicación no debe terminar cuando este contador es distinto de cero. Si el contador es distinto de cero, la ventana principal de la aplicación se oculta (no se destruye) cuando el usuario elige Cerrar en el menú del sistema o Salir en el menú Archivo. El marco de `CFrameWnd::OnClose`trabajo llama a esta función en .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Recupera el filtro de mensajes actual de la aplicación.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al filtro de mensajes actual.

### <a name="remarks"></a>Observaciones

Llame a esta función para tener acceso al objeto derivado actual, `COleMessageFilter`tal como se llamaría para tener `AfxGetApp` acceso al objeto de aplicación actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Recupera el indicador de control de usuario actual.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario tiene el control de la aplicación; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El usuario tiene el control de la aplicación cuando el usuario ha abierto o creado explícitamente un nuevo documento. El usuario también tiene el control si la aplicación no fue iniciada por los archivos DLL del sistema OLE, es decir, si el usuario inició la aplicación con el shell del sistema.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Establece o borra el indicador de control de usuario, `AfxOleGetUserCtrl`que se explica en la referencia para .

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parámetros

*bUserCtrl*<br/>
Especifica si se debe establecer o borrar el indicador de control de usuario.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función cuando el usuario crea o carga un documento, pero no cuando se carga o crea un documento a través de una acción indirecta, como cargar un objeto incrustado desde una aplicación contenedora.

Llame a esta función si otras acciones de la aplicación deben poner al usuario en control de la aplicación.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp

Incrementa el recuento global del marco de trabajo del número de objetos activos en la aplicación.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo mantiene un recuento del número de objetos activos en una aplicación. Las `AfxOleLockApp` `AfxOleUnlockApp` funciones y, respectivamente, incrementan y disminuyen este recuento.

Cuando el usuario intenta cerrar una aplicación que tiene objetos activos (una aplicación para la que el recuento de objetos activos es distinto de cero), el marco de trabajo oculta la aplicación de la vista del usuario en lugar de cerrarla por completo. La `AfxOleCanExitApp` función indica si la aplicación puede finalizar.

Llamada `AfxOleLockApp` desde cualquier objeto que expone interfaces OLE, si sería indeseable que ese objeto se destruya mientras que todavía lo usa una aplicación cliente. `AfxOleUnlockApp` Llame también al destructor de `AfxOleLockApp` cualquier objeto que llame al constructor. De forma `COleDocument` predeterminada, (y las clases derivadas) bloquean y desbloquean automáticamente la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp

Disminuye el recuento de objetos activos del marco de trabajo en la aplicación.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Observaciones

Consulte `AfxOleLockApp` para obtener más información.

Cuando el número de objetos activos llega a cero, `AfxOleOnReleaseAllObjects` se llama.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Bloquea el generador de clases del control especificado para que los datos creados dinámicamente asociados con el control permanezcan en memoria.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase único del control.

*lpszProgID*<br/>
El ID de programa único del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control se bloqueó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esto puede acelerar significativamente la visualización de los controles. Por ejemplo, una vez que cree un control `AfxOleLockControl`en un cuadro de diálogo y bloquee el control con , no es necesario crearlo y eliminarlo de nuevo cada vez que se muestre o destruya el cuadro de diálogo. Si el usuario abre y cierra un cuadro de diálogo repetidamente, bloquear los controles puede mejorar significativamente el rendimiento. Cuando esté listo para destruir `AfxOleUnlockControl`el control, llame a .

### <a name="example"></a>Ejemplo

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Esta función le permite registrar el servidor en el registro del sistema OLE.

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
Referencia al identificador de clase OLE del servidor.

*lpszClassName*<br/>
Puntero a una cadena que contiene el nombre de clase de los objetos del servidor.

*lpszShortTypeName*<br/>
Puntero a una cadena que contiene el nombre corto del tipo de objeto del servidor, como "Chart."

*lpszLongTypeName*<br/>
Puntero a una cadena que contiene el nombre largo del tipo de objeto del servidor, como "Gráfico de Microsoft Excel 5.0."

*nAppType*<br/>
Un valor, tomado de la enumeración OLE_APPTYPE, especificando el tipo de aplicación OLE. A continuación se indican los posibles valores:

- OAT_INPLACE_SERVER Server tiene una interfaz de usuario de servidor completa.

- OAT_SERVER Server solo admite la inserción.

- OAT_CONTAINER Container admite vínculos a incrustaciones.

- OAT_DISPATCH_OBJECT `IDispatch`objeto capaz.

*rglpszRegister*<br/>
Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE si no se encuentra ningún valor existente para las claves.

*rglpszOverwrite*<br/>
Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE si el registro contiene valores existentes para las claves dadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la clase de servidor se registra correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La mayoría `COleTemplateServer::Register` de las aplicaciones pueden usar para registrar los tipos de documentos de la aplicación. Si el formato de registro del sistema de la aplicación `AfxOleRegisterServerClass` no se ajusta al patrón típico, puede usar para obtener más control.

El registro consta de un conjunto de claves y valores. Los *argumentos rglpszRegister* y *rglpszOverwrite* son matrices de punteros a cadenas, cada una `'\0'`de las que consta de una clave y un valor separados por un carácter **NULL** ( ). Cada una de estas cadenas puede tener parámetros reemplazables cuyos lugares están marcados por las secuencias de caracteres *%1* a *%5*.

Los símbolos se rellenan de la siguiente manera:

|Símbolo|Value|
|------------|-----------|
|%1|ID de clase, formateado como una cadena|
|%2|Nombre de la clase|
|%3|Ruta de acceso al archivo ejecutable|
|%4|Nombre de tipo corto|
|%5|Nombre de tipo largo|

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementa la interfaz de usuario para el comando *typename* Object.

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
Un puntero al elemento OLE del cliente.

*pMenu*<br/>
Puntero al objeto de menú que se va a actualizar.

*iMenuItem*<br/>
El índice del elemento de menú que se va a actualizar.

*nIDVerbMin*<br/>
El identificador de comando que corresponde al verbo principal.

*nIDVerbMax*<br/>
El identificador de comando que corresponde al último verbo.

*nIDConvert*<br/>
ID del elemento de menú Convertir.

### <a name="remarks"></a>Observaciones

Si el servidor reconoce solo un verbo principal, el elemento de menú se convierte en "verb *typename* Object" y el comando *nIDVerbMin* se envía cuando el usuario elige el comando. Si el servidor reconoce varios verbos, el elemento de menú se convierte en " *typename* Object" y aparece un submenú que enumera todos los verbos cuando el usuario elige el comando. Cuando el usuario elige un verbo del submenú, se envía *nIDVerbMin* si se elige el primer verbo, se envía *nIDVerbMin* + 1 si se elige el segundo verbo, etc. La `COleDocument` implementación predeterminada controla automáticamente esta característica.

Debe tener la siguiente instrucción en el script de recursos de aplicación del cliente (. RC) archivo:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>Requisitos

**Encabezado**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Desbloquea el generador de clases del control especificado.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
El identificador de clase único del control.

*lpszProgID*<br/>
El ID de programa único del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control se ha desbloqueado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un control está `AfxOleLockControl`bloqueado con , para que los datos creados dinámicamente asociados con el control permanezcan en la memoria. Esto puede acelerar significativamente la visualización del control porque el control no es necesario creary destruir cada vez que se muestra. Cuando esté listo para destruir `AfxOleUnlockControl`el control, llame a .

### <a name="example"></a>Ejemplo

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
