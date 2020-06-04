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
ms.openlocfilehash: b678c8a46f56337d76ec192869449797a4f66fb3
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168803"
---
# <a name="catlexemodulet-class"></a>Clase CAtlExeModuleT

Esta clase representa el módulo para una aplicación.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlExeModuleT`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlExeModuleT:: CAtlExeModuleT](#catlexemodulet)|El constructor.|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlExeModuleT:: InitializeCom](#initializecom)|Inicializa COM.|
|[CAtlExeModuleT::P arseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro si es necesario.|
|[CAtlExeModuleT::P ostMessageLoop](#postmessageloop)|Se llama a este método inmediatamente después de que se cierre el bucle de mensajes.|
|[CAtlExeModuleT::P reMessageLoop](#premessageloop)|Se llama a este método inmediatamente antes de entrar en el bucle de mensajes.|
|[CAtlExeModuleT:: RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase.|
|[CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase.|
|[CAtlExeModuleT:: Run](#run)|Este método ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y realizar la limpieza.|
|[CAtlExeModuleT:: RunMessageLoop](#runmessageloop)|Este método ejecuta el bucle de mensajes.|
|[CAtlExeModuleT:: UninitializeCom](#uninitializecom)|Desinicializa COM.|
|[CAtlExeModuleT:: Unlock](#unlock)|Disminuye el recuento de bloqueos del módulo.|
|[CAtlExeModuleT:: WinMain](#winmain)|Este método implementa el código necesario para ejecutar un archivo EXE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)|Marca que indica que debe haber un retraso al cerrar el módulo.|
|[CAtlExeModuleT:: m_dwPause](#m_dwpause)|Un valor de pausa que se usa para asegurarse de que todos los objetos se liberan antes del cierre.|
|[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)|Un valor de tiempo de espera que se usa para retrasar la descarga del módulo.|

## <a name="remarks"></a>Observaciones

`CAtlExeModuleT`representa el módulo para una aplicación (EXE) y contiene código que admite la creación de un archivo EXE, el procesamiento de la línea de comandos, el registro de objetos de clase, la ejecución del bucle de mensajes y la limpieza al salir.

Esta clase está diseñada para mejorar el rendimiento cuando se crean y destruyen continuamente objetos COM en el servidor EXE. Una vez liberado el último objeto COM, el archivo EXE espera una duración especificada por el miembro de datos [CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout) . Si no hay ninguna actividad durante este período (es decir, no se crea ningún objeto COM), se inicia el proceso de cierre.

El miembro de datos [CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown) es una marca que se usa para determinar si el archivo exe debe utilizar el mecanismo definido anteriormente. Si se establece en false, el módulo se terminará inmediatamente.

Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT:: CAtlExeModuleT

El constructor.

```cpp
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Si no se pudo inicializar el módulo EXE, WinMain se devolverá inmediatamente sin más procesamiento.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

Destructor.

```cpp
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT:: InitializeCom

Inicializa COM.

```cpp
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método se llama desde el constructor y se puede invalidar para inicializar COM de forma distinta de la implementación predeterminada. La implementación predeterminada llama a `CoInitializeEx(NULL, COINIT_MULTITHREADED)` o `CoInitialize(NULL)` , dependiendo de la configuración del proyecto.

La invalidación de este método normalmente requiere invalidar [CAtlExeModuleT:: UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT:: m_bDelayShutdown

Marca que indica que debe haber un retraso al cerrar el módulo.

```cpp
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Observaciones

Vea la [información general de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) para más información.

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT:: m_dwPause

Un valor de pausa que se usa para asegurarse de que todos los objetos desaparecen antes del cierre.

```cpp
DWORD m_dwPause;
```

### <a name="remarks"></a>Observaciones

Cambie este valor después de llamar a [CAtlExeModuleT:: InitializeCom](#initializecom) para establecer el número de milisegundos usados como el valor de pausa para cerrar el servidor. El valor predeterminado es 1000 milisegundos.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT:: m_dwTimeOut

Un valor de tiempo de espera que se usa para retrasar la descarga del módulo.

```cpp
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Observaciones

Cambie este valor después de llamar a [CAtlExeModuleT:: InitializeCom](#initializecom) para definir el número de milisegundos usados como el valor de tiempo de espera para cerrar el servidor. El valor predeterminado es 5000 milisegundos. Vea la [información general de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) para obtener más información.

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::P arseCommandLine

Analiza la línea de comandos y realiza el registro si es necesario.

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
Línea de comandos que se pasa a la aplicación.

*pnRetCode*<br/>
HRESULT correspondiente al registro (si tuvo lugar).

### <a name="return-value"></a>Valor devuelto

Devuelva true si la aplicación debe continuar ejecutándose; de lo contrario, false.

### <a name="remarks"></a>Observaciones

Este método se llama desde [CAtlExeModuleT:: WinMain](#winmain) y se puede invalidar para controlar los modificadores de la línea de comandos. La implementación predeterminada comprueba los argumentos de la línea de comandos **/regserver** y **modificador/unregserver** y realiza el registro o la anulación del registro.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::P ostMessageLoop

Se llama a este método inmediatamente después de que se cierre el bucle de mensajes.

```cpp
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Invalide este método para realizar una limpieza de aplicaciones personalizada. La implementación predeterminada llama a [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects).

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::P reMessageLoop

Se llama a este método inmediatamente antes de entrar en el bucle de mensajes.

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
El valor que se pasa como parámetro *nShowCmd* en WinMain.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Invalide este método para agregar código de inicialización personalizado para la aplicación. La implementación predeterminada registra los objetos de clase.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT:: RegisterClassObjects

Registra el objeto de clase con OLE para que otras aplicaciones puedan conectarse a él.

```cpp
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parámetros

*dwClsContext*<br/>
Especifica el contexto en el que se va a ejecutar el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, S_FALSE si no hay ninguna clase para registrar o un error HRESULT en caso de error.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT:: RevokeClassObjects

Quita el objeto de clase.

```cpp
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, S_FALSE si no hay ninguna clase para registrar o un error HRESULT en caso de error.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT:: Run

Este método ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y realizar la limpieza.

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método se puede invalidar. Sin embargo, en la práctica es mejor reemplazar [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)o [CAtlExeModuleT::P ostmessageloop](#postmessageloop) en su lugar.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT:: RunMessageLoop

Este método ejecuta el bucle de mensajes.

```cpp
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Observaciones

Este método se puede invalidar para cambiar el comportamiento del bucle de mensajes.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT:: UninitializeCom

Desinicializa COM.

```cpp
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método simplemente llama a [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) y se llama desde el destructor. Invalide este método si invalida [CAtlExeModuleT:: InitializeCom](#initializecom).

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT:: Unlock

Disminuye el recuento de bloqueos del módulo.

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT:: WinMain

Este método implementa el código necesario para ejecutar un archivo EXE.

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del archivo ejecutable.

### <a name="remarks"></a>Observaciones

Este método se puede invalidar. Si invalide [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT::P ostmessageloop](#postmessageloop)o [CAtlExeModuleT:: RunMessageLoop](#runmessageloop) no proporciona suficiente flexibilidad, es posible invalidar la `WinMain` función mediante este método.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Clase CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
