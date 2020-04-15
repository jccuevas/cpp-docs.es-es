---
title: Clase CAtlExeModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: a20a02a467d74a89e3cda176a6a15961be4ffd61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318989"
---
# <a name="catlexemodulet-class"></a>Clase CAtlExeModuleT

Esta clase representa el módulo de una aplicación.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada `CAtlExeModuleT`de .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|El constructor.|
|[CAtlExeModuleT::-CAtlExeModuleT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlexeModuleT::InitializeCom](#initializecom)|Inicializa COM.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro si es necesario.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Este método se llama inmediatamente después de que se cierra el bucle de mensajes.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Este método se llama inmediatamente antes de escribir el bucle de mensajes.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase.|
|[CAtlExeModuleT::Ejecutar](#run)|Este método ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y limpiar.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Este método ejecuta el bucle de mensajes.|
|[CAtlexeModuleT::UninitializeCom](#uninitializecom)|Uninitializes COM.|
|[CAtlExeModuleT::Unlock](#unlock)|Disminuye el recuento de bloqueos del módulo.|
|[CAtlExeModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar un archivo EXE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Un indicador que indica que debe haber un retraso al apagar el módulo.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Valor de pausa utilizado para asegurarse de que todos los objetos se liberan antes del apagado.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Un valor de tiempo de espera utilizado para retrasar la descarga del módulo.|

## <a name="remarks"></a>Observaciones

`CAtlExeModuleT`representa el módulo de una aplicación (EXE) y contiene código que admite la creación de un archivo EXE, el procesamiento de la línea de comandos, el registro de objetos de clase, la ejecución del bucle de mensajes y la limpieza al salir.

Esta clase está diseñada para mejorar el rendimiento cuando los objetos COM en el servidor EXE se crean y destruyen continuamente. Después de liberar el último objeto COM, exe espera una duración especificada por el [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) miembro de datos. Si no hay ninguna actividad durante este período (es decir, no se crea ningún objeto COM), se inicia el proceso de apagado.

El [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) miembro de datos es un indicador utilizado para determinar si el EXE debe utilizar el mecanismo definido anteriormente. Si se establece en false, el módulo finalizará inmediatamente.

Para obtener más información sobre los módulos de ATL, consulte Clases de [módulo ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

El constructor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Si no se pudo inicializar el módulo EXE, WinMain volverá inmediatamente sin más procesamiento.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT::-CAtlExeModuleT

Destructor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlexeModuleT::InitializeCom

Inicializa COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método se llama desde el constructor y se puede invalidar para inicializar COM de una manera diferente de la implementación predeterminada. La implementación `CoInitializeEx(NULL, COINIT_MULTITHREADED)` predeterminada `CoInitialize(NULL)` llama o depende de la configuración del proyecto.

Reemplazar este método normalmente requiere reemplazar [CAtlExeModuleT::UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown

Un indicador que indica que debe haber un retraso al apagar el módulo.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Observaciones

Consulte la información general de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) para obtener más información.

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause

Un valor de pausa utilizado para asegurarse de que todos los objetos han desaparecido antes del apagado.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Observaciones

Cambie este valor después de llamar a [CAtlExeModuleT::InitializeCom](#initializecom) para establecer el número de milisegundos utilizados como valor de pausa para apagar el servidor. El valor predeterminado es 1000 milisegundos.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut

Un valor de tiempo de espera utilizado para retrasar la descarga del módulo.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Observaciones

Cambie este valor después de llamar a [CAtlExeModuleT::InitializeCom](#initializecom) para definir el número de milisegundos utilizados como valor de tiempo de espera para cerrar el servidor. El valor predeterminado es 5000 milisegundos. Consulte la información general de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) para obtener más detalles.

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine

Analiza la línea de comandos y realiza el registro si es necesario.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
La línea de comandos se pasa a la aplicación.

*pnRetCode*<br/>
El HRESULT correspondiente al registro (si se llevó a cabo).

### <a name="return-value"></a>Valor devuelto

Devuelve true si la aplicación debe continuar ejecutándose, de lo contrario false.

### <a name="remarks"></a>Observaciones

Se llama a este método desde [CAtlExeModuleT::WinMain](#winmain) y se puede invalidar para controlar los modificadores de línea de comandos. La implementación predeterminada comprueba los argumentos de línea de comandos **/RegServer** y **/UnRegServer** y realiza el registro o la anulación del registro.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

Este método se llama inmediatamente después de que se cierra el bucle de mensajes.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Invalide este método para realizar la limpieza de la aplicación personalizada. La implementación predeterminada llama a [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop

Este método se llama inmediatamente antes de escribir el bucle de mensajes.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
El valor pasado como el *nShowCmd* parámetro en WinMain.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Invalide este método para agregar código de inicialización personalizado para la aplicación. La implementación predeterminada registra los objetos de clase.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Registra el objeto de clase con OLE para que otras aplicaciones puedan conectarse a él.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parámetros

*dwClsContext*<br/>
Especifica el contexto en el que se va a ejecutar el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Determina los tipos de conexión al objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito, S_FALSE si no había clases para registrarse o un error HRESULT en caso de error.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Quita el objeto de clase.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito, S_FALSE si no había clases para registrarse o un error HRESULT en caso de error.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Ejecutar

Este método ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y limpiar.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se va a mostrar la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método se puede invalidar. Sin embargo, en la práctica es mejor reemplazar [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop)o [CAtlExeModuleT::PostMessageLoop](#postmessageloop) en su lugar.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Este método ejecuta el bucle de mensajes.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Observaciones

Este método se puede invalidar para cambiar el comportamiento del bucle de mensajes.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlexeModuleT::UninitializeCom

Uninitializes COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método simplemente llama a [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) y se llama desde el destructor. Invalide este método si reemplaza [CAtlExeModuleT::InitializeCom](#initializecom).

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Unlock

Disminuye el recuento de bloqueos del módulo.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain

Este método implementa el código necesario para ejecutar un archivo EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se va a mostrar la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del ejecutable.

### <a name="remarks"></a>Observaciones

Este método se puede invalidar. Si reemplazar [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop)o [CAtlExeModuleT::RunMessageLoop](#runmessageloop) no proporciona suficiente flexibilidad, es `WinMain` posible invalidar la función mediante este método.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Clase CAtlDllModulet](../../atl/reference/catldllmodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
