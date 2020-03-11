---
title: Control de la aplicación
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855699"
---
# <a name="application-control"></a>Control de la aplicación

OLE requiere un control considerable sobre las aplicaciones y sus objetos. Los archivos DLL del sistema OLE deben poder iniciar y liberar las aplicaciones automáticamente, coordinar su producción y modificar los objetos, etc. Las funciones de este tema cumplen estos requisitos. Además de ser llamado por los archivos DLL del sistema OLE, las aplicaciones también deben llamar a estas funciones a veces.

### <a name="application-control"></a>Control de la aplicación

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Indica si la aplicación puede finalizar.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Recupera el filtro de mensajes actual de la aplicación.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Recupera la marca de control de usuario actual.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Establece o borra la marca de control de usuario.|
|[AfxOleLockApp](#afxolelockapp)|Incrementa el recuento global del marco de trabajo del número de objetos activos en una aplicación.|
|[AfxOleLockControl](#afxolelockcontrol)| Bloquea el generador de clases del control especificado. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Disminuye el recuento de la plataforma del número de objetos activos en una aplicación.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Desbloquea el generador de clases del control especificado. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Registra un servidor en el registro del sistema OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementa la interfaz de usuario para el comando de objeto *TypeName* .|

##  <a name="afxolecanexitapp"></a>AfxOleCanExitApp

Indica si la aplicación puede finalizar.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la aplicación puede salir; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una aplicación no debe terminar si hay referencias pendientes a sus objetos. Las funciones globales `AfxOleLockApp` y `AfxOleUnlockApp` incremento y decremento, respectivamente, un contador de referencias a los objetos de la aplicación. La aplicación no debe terminar cuando este contador es distinto de cero. Si el contador es distinto de cero, la ventana principal de la aplicación se oculta (no se destruye) cuando el usuario elige cerrar en el menú del sistema o salir del menú archivo. El marco de trabajo llama a esta función en `CFrameWnd::OnClose`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Recupera el filtro de mensajes actual de la aplicación.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Valor devuelto

Puntero al filtro de mensajes actual.

### <a name="remarks"></a>Observaciones

Llame a esta función para tener acceso al objeto actual derivado de `COleMessageFilter`, del mismo modo que llamaría a `AfxGetApp` para tener acceso al objeto de aplicación actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: AFXWIN. h

##  <a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Recupera la marca de control de usuario actual.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario tiene el control de la aplicación; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El usuario tiene el control de la aplicación cuando el usuario ha abierto o creado explícitamente un nuevo documento. El usuario también tiene control si la aplicación no se inició con los archivos DLL del sistema OLE (es decir, si el usuario inició la aplicación con el Shell del sistema).

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Establece o borra la marca de control de usuario, que se explica en la referencia de `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parámetros

*bUserCtrl*<br/>
Especifica si se va a establecer o borrar la marca de control de usuario.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función cuando el usuario crea o carga un documento, pero no cuando se carga o se crea un documento a través de una acción indirecta, como la carga de un objeto incrustado desde una aplicación contenedora.

Llame a esta función si otras acciones de la aplicación deben poner al usuario en el control de la aplicación.

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="afxolelockapp"></a>AfxOleLockApp

Incrementa el recuento global del marco de trabajo del número de objetos activos en la aplicación.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo mantiene un recuento del número de objetos activos en una aplicación. Las funciones `AfxOleLockApp` y `AfxOleUnlockApp`, respectivamente, aumentan y disminuyen este recuento.

Cuando el usuario intenta cerrar una aplicación que tiene objetos activos (una aplicación para la que el número de objetos activos es distinto de cero), el marco de trabajo oculta la aplicación de la vista del usuario en lugar de cerrarla por completo. La función `AfxOleCanExitApp` indica si la aplicación puede finalizar.

Llame a `AfxOleLockApp` desde cualquier objeto que exponga interfaces OLE, en caso de que no sea deseable que ese objeto se destruya mientras se sigue usando una aplicación cliente. Llame también a `AfxOleUnlockApp` en el destructor de cualquier objeto que llame a `AfxOleLockApp` en el constructor. De forma predeterminada, `COleDocument` (y las clases derivadas) bloquean y desbloquean la aplicación automáticamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="afxoleunlockapp"></a>AfxOleUnlockApp

Disminuye el recuento de objetos activos de la aplicación en el marco de trabajo.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Observaciones

Consulte `AfxOleLockApp` para obtener más información.

Cuando el número de objetos activos llega a cero, se llama a `AfxOleOnReleaseAllObjects`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Bloquea el generador de clases del control especificado para que los datos creados dinámicamente asociados al control permanezcan en la memoria.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
IDENTIFICADOR de clase único del control.

*lpszProgID*<br/>
IDENTIFICADOR del programa único del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control se ha bloqueado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esto puede acelerar considerablemente la presentación de los controles. Por ejemplo, una vez que se crea un control en un cuadro de diálogo y se bloquea el control con `AfxOleLockControl`, no es necesario crearlo y eliminarlo de nuevo cada vez que se muestra o se destruye el cuadro de diálogo. Si el usuario abre y cierra repetidamente un cuadro de diálogo, el bloqueo de los controles puede mejorar considerablemente el rendimiento. Cuando esté listo para destruir el control, llame a `AfxOleUnlockControl`.

### <a name="example"></a>Ejemplo

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

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

*CLSID*<br/>
Referencia al identificador de clase OLE del servidor.

*lpszClassName*<br/>
Puntero a una cadena que contiene el nombre de clase de los objetos del servidor.

*lpszShortTypeName*<br/>
Puntero a una cadena que contiene el nombre corto del tipo de objeto del servidor, como "gráfico".

*lpszLongTypeName*<br/>
Puntero a una cadena que contiene el nombre largo del tipo de objeto del servidor, como "gráfico de Microsoft Excel 5,0".

*nAppType*<br/>
Un valor, tomado de la enumeración OLE_APPTYPE, que especifica el tipo de aplicación OLE. A continuación se indican los posibles valores:

- OAT_INPLACE_SERVER Server tiene una interfaz de usuario de servidor completa.

- OAT_SERVER Server solo admite la incrustación.

- OAT_CONTAINER contenedor admite vínculos a las incrustaciones.

- OAT_DISPATCH_OBJECT objeto compatible con `IDispatch`.

*rglpszRegister*<br/>
Matriz de punteros a cadenas que representan las claves y los valores que se van a agregar al registro del sistema OLE si no se encuentran valores existentes para las claves.

*rglpszOverwrite*<br/>
Matriz de punteros a cadenas que representan las claves y los valores que se van a agregar al registro del sistema OLE si el registro contiene valores existentes para las claves especificadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la clase de servidor se ha registrado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La mayoría de las aplicaciones pueden usar `COleTemplateServer::Register` para registrar los tipos de documento de la aplicación. Si el formato del registro del sistema de la aplicación no se ajusta al patrón típico, puede usar `AfxOleRegisterServerClass` para obtener más control.

El registro está formado por un conjunto de claves y valores. Los argumentos *rglpszRegister* y *rglpszOverwrite* son matrices de punteros a cadenas, cada una de las cuales consta de una clave y un valor separado por un carácter **nulo** (`'\0'`). Cada una de estas cadenas puede tener parámetros reemplazables cuyos lugares estén marcados por las secuencias de caracteres de *%1* a *%5*.

Los símbolos se rellenan de la siguiente manera:

|Símbolo|Value|
|------------|-----------|
|%1|IDENTIFICADOR de clase, con formato de cadena|
|%2|Nombre de clase|
|%3|Ruta de acceso al archivo ejecutable|
|%4|Nombre de tipo corto|
|%5|Nombre de tipo largo|

### <a name="requirements"></a>Requisitos

**Encabezado**: afxdisp. h

##  <a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementa la interfaz de usuario para el comando de objeto *TypeName* .

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
Puntero al elemento OLE del cliente.

*pMenu*<br/>
Puntero al objeto de menú que se va a actualizar.

*iMenuItem*<br/>
Índice del elemento de menú que se va a actualizar.

*nIDVerbMin*<br/>
IDENTIFICADOR de comando que corresponde al verbo principal.

*nIDVerbMax*<br/>
IDENTIFICADOR de comando que corresponde al último verbo.

*nIDConvert*<br/>
IDENTIFICADOR del elemento de menú Convert.

### <a name="remarks"></a>Observaciones

Si el servidor reconoce solo un verbo principal, el elemento de menú se convierte en "verbo *TypeName* Object" y el comando *nIDVerbMin* se envía cuando el usuario elige el comando. Si el servidor reconoce varios verbos, el elemento de menú se convierte en " *TypeName* Object" y un submenú que enumera todos los verbos aparecen cuando el usuario elige el comando. Cuando el usuario elige un verbo en el submenú, se envía *nIDVerbMin* si se elige el primer verbo, se envía *nIDVerbMin* + 1 si se elige el segundo verbo, y así sucesivamente. La implementación de `COleDocument` predeterminada controla automáticamente esta característica.

Debe tener la siguiente instrucción en el script de recursos de aplicación de su cliente (. RC):

**#include \<afxolecl. RC >**

### <a name="requirements"></a>Requisitos

**Encabezado**: afxole. h

## <a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Desbloquea el generador de clases del control especificado.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
IDENTIFICADOR de clase único del control.

*lpszProgID*<br/>
IDENTIFICADOR del programa único del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador de clases del control se desbloqueó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Un control está bloqueado con `AfxOleLockControl`, de modo que los datos creados dinámicamente asociados al control permanecen en la memoria. Esto puede acelerar significativamente la visualización del control porque no es necesario crearlo ni destruirlo cada vez que se muestra. Cuando esté listo para destruir el control, llame a `AfxOleUnlockControl`.

### <a name="example"></a>Ejemplo

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
