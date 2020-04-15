---
title: Clase CAtlServiceModuleT
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 5d87eada997d0bbfe44cd07a819f6b012a7a3a20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321337"
---
# <a name="catlservicemodulet-class"></a>Clase CAtlServiceModuleT

Esta clase implementa un servicio.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada `CAtlServiceModuleT`de .

*nServiceNameID*<br/>
Identificador de recursos del servicio.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|La rutina de controlador para el servicio.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Proporciona la configuración de seguridad predeterminada para el servicio.|
|[CAtlServiceModuleT::Instalar](#install)|Instala y crea el servicio.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Confirma que el servicio se ha instalado.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Escribe en el registro de eventos.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Invalide este método para continuar con el servicio.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Invalide este método para interrogar el servicio.|
|[CAtlServiceModuleT::OnPause](#onpause)|Invalide este método para pausar el servicio.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Invalide este método para cerrar el servicio|
|[CAtlServiceModuleT::OnStop](#onstop)|Invalide este método para detener el servicio|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Invalide este método para controlar solicitudes desconocidas al servicio|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro si es necesario.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Este método se llama inmediatamente antes de escribir el bucle de mensajes.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registra el servicio en el registro.|
|[CAtlServiceModuleT::Run](#run)|Ejecuta el servicio.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|El método al que llama el Administrador de control de servicios.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Actualiza el estado del servicio.|
|[CAtlServiceModuleT::Start](#start)|Llamado `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Detiene y quita el servicio.|
|[CAtlServiceModuleT::Unlock](#unlock)|Disminuye el recuento de bloqueos del servicio.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Quita el servicio del registro.|
|[CAtlServiceModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar el servicio.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Marcador que indica que el programa se está ejecutando como un servicio.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Variable miembro que almacena el identificador de subproceso.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Variable miembro que almacena un identificador en la estructura de información de estado para el servicio actual.|
|[CAtlServiceModuleT::m_status](#m_status)|Variable miembro que almacena la estructura de información de estado para el servicio actual.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|El nombre del servicio que se está registrando.|

## <a name="remarks"></a>Observaciones

`CAtlServiceModuleT`, derivado de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementa un módulo de servicio ATL. `CAtlServiceModuleT`proporciona métodos para el procesamiento, la instalación, el registro y la eliminación de la línea de comandos. Si se requiere funcionalidad adicional, estos y otros métodos se pueden invalidar.

Esta clase reemplaza la clase [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL. Consulte [Clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlexeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT

El constructor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos y establece el estado inicial del servicio.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::Handler

La rutina de controlador para el servicio.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Un modificador que define la operación de controlador. Para obtener más información, consulte Comentarios.

### <a name="remarks"></a>Observaciones

Este es el código al que llama Service Control Manager (SCM) para recuperar el estado del servicio y emitir instrucciones como detener o pausar. El SCM pasa un código de `Handler` operación, que se muestra a continuación, para indicar lo que el servicio debe hacer.

|Código de operación|Significado|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|detiene el servicio. Invalide el método [CAtlServiceModuleT::OnStop](#onstop) en atlbase.h para cambiar el comportamiento.|
|SERVICE_CONTROL_PAUSE|Usuario implementado. Invalide el método vacío [CAtlServiceModuleT::OnPause](#onpause) en atlbase.h para pausar el servicio.|
|SERVICE_CONTROL_CONTINUE|Usuario implementado. Invalide el método vacío [CAtlServiceModuleT::OnContinue](#oncontinue) in atlbase.h para continuar con el servicio.|
|SERVICE_CONTROL_INTERROGATE|Usuario implementado. Invalide el método vacío [CAtlServiceModuleT::OnInterrogate](#oninterrogate) en atlbase.h para interrogar el servicio.|
|SERVICE_CONTROL_SHUTDOWN|Usuario implementado. Invalide el método vacío [CAtlServiceModuleT::OnShutdown](#onshutdown) en atlbase.h para apagar el servicio.|

Si no se reconoce el código de operación, se llama al método [CAtlServiceModuleT::OnUnknownRequest.](#onunknownrequest)

Un servicio predeterminado generado por ATL solo controla la instrucción stop. Si el SCM pasa la instrucción stop, el servicio le dice al SCM que el programa está a punto de detenerse. A continuación, `PostThreadMessage` el servicio llama para publicar un mensaje de cierre en sí mismo. Esto termina el bucle de mensajes y el servicio se cerrará en última instancia.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity

Proporciona la configuración de seguridad predeterminada para el servicio.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Cualquier clase que `CAtlServiceModuleT` deriva de debe implementar este método en la clase derivada.

Utilice la autenticación de nivel PKT, el nivel de suplantación de `CoInitializeSecurity`RPC_C_IMP_LEVEL_IDENTIFY y un descriptor de seguridad no nulo adecuado en la llamada a .

Para proyectos de servicio no atribuidos generados por el asistente, esto sería en

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Para los proyectos de servicio atribuidos, esto sería en

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT::Instalar

Instala y crea el servicio.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Instala el servicio en la base de datos de Service Control Manager (SCM) y, a continuación, crea el objeto de servicio. Si no se pudo crear el servicio, se muestra un cuadro de mensaje y el método devuelve FALSE.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled

Confirma que el servicio se ha instalado.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el servicio está instalado, FALSE en caso contrario.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::LogEvent

Escribe en el registro de eventos.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena que se va a escribir en el registro de eventos.

*...*<br/>
Cadenas adicionales opcionales que se escribirán en el registro de eventos.

### <a name="remarks"></a>Observaciones

Este método escribe detalles en un registro de eventos mediante la función [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Si no se está ejecutando ningún servicio, la cadena se envía a la consola.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT::m_bService

Marcador que indica que el programa se está ejecutando como un servicio.

```
BOOL m_bService;
```

### <a name="remarks"></a>Observaciones

Se utiliza para distinguir un EXE de servicio de un EXE de aplicación.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID

Variable miembro que almacena el identificador de subproceso del servicio.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Observaciones

Esta variable almacena el identificador de subproceso del subproceso actual.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus

Variable miembro que almacena un identificador en la estructura de información de estado para el servicio actual.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Observaciones

La estructura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contiene información sobre un servicio.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT::m_status

Variable miembro que almacena la estructura de información de estado para el servicio actual.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Observaciones

La estructura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contiene información sobre un servicio.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName

El nombre del servicio que se está registrando.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Observaciones

Cadena terminada en null que almacena el nombre del servicio.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT::OnContinue

Invalide este método para continuar con el servicio.

```
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate

Invalide este método para interrogar el servicio.

```
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT::OnPause

Invalide este método para pausar el servicio.

```
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown

Invalide este método para cerrar el servicio.

```
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT::OnStop

Invalide este método para detener el servicio.

```
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest

Invalide este método para controlar las solicitudes desconocidas al servicio.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Reservado.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine

Analiza la línea de comandos y realiza el registro si es necesario.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
Línea de comandos.

*pnRetCode*<br/>
El HRESULT correspondiente al registro (si se llevó a cabo).

### <a name="return-value"></a>Valor devuelto

Devuelve true en caso de éxito o false si no se pudo registrar el archivo RGS proporcionado en la línea de comandos.

### <a name="remarks"></a>Observaciones

Analiza la línea de comandos y registra o anula el registro del archivo RGS suministrado si es necesario. Este método llama a [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) para comprobar **/RegServer** y **/UnregServer**. Agregar el argumento **-/Service** registrará el servicio.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop

Este método se llama inmediatamente antes de escribir el bucle de mensajes.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Este parámetro se pasa a [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Invalide este método para agregar código de inicialización personalizado para el servicio.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId

Registra el servicio en el registro.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parámetros

*bServicio*<br/>
Debe ser cierto para registrarse como un servicio.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT::Run

Ejecuta el servicio.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se va a mostrar la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Después de `Run` llamarse, llama a [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)y [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT::ServiceMain

El Administrador de control de servicios llama a este método.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parámetros

*dwArgc*<br/>
El argumento argc.

*lpszArgv*<br/>
El argumento argv.

### <a name="remarks"></a>Observaciones

El Administrador de control de `ServiceMain` servicios (SCM) llama al abrir la aplicación Servicios en el Panel de control, seleccione el servicio y haga clic en Iniciar.

Después de `ServiceMain`las llamadas de SCM , un servicio debe proporcionar al SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (como pausar o detener). Posteriormente, [CAtlServiceModuleT::Run](#run) se llama para realizar el trabajo principal del servicio. `Run`continúa ejecutándose hasta que se detiene el servicio.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus

Este método actualiza el estado del servicio.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parámetros

*dwState*<br/>
Nuevo estado. Consulte [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) para ver los valores posibles.

### <a name="remarks"></a>Observaciones

Actualiza la información de estado del Administrador de control de servicio para el servicio. Se llama mediante [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) y otros métodos de controlador. El estado también se almacena en la variable miembro [CAtlServiceModuleT::m_status](#m_status).

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT::Start

Llamado `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se va a mostrar la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El [método CAtlServiceModuleT::WinMain](#winmain) controla tanto el registro como la instalación, así como las tareas implicadas en la eliminación de entradas del Registro y la desinstalación del módulo. Cuando se ejecuta `WinMain` el `Start`servicio, llama a .

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::Uninstall

Detiene y quita el servicio.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Detiene la ejecución del servicio y lo quita de la base de datos de Service Control Manager.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT::Unlock

Disminuye el recuento de bloqueos del servicio.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el recuento de bloqueos, que puede ser útil para el diagnóstico y la depuración.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId

Quita el servicio del registro.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::WinMain

Este método implementa el código necesario para iniciar el servicio.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se va a mostrar la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del servicio.

### <a name="remarks"></a>Observaciones

Este método procesa la línea de comandos (con [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) y, a continuación, inicia el servicio (mediante [CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Consulte también

[Clase CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
