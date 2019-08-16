---
title: CAtlServiceModuleT (clase)
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
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497736"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT (clase)

Esta clase implementa un servicio.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlServiceModuleT`.

*nServiceNameID*<br/>
Identificador de recurso del servicio.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|La rutina de controlador para el servicio.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Proporciona la configuración de seguridad predeterminada para el servicio.|
|[CAtlServiceModuleT::Install](#install)|Instala y crea el servicio.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Confirma que se ha instalado el servicio.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Escribe en el registro de eventos.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Invalide este método para continuar el servicio.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Invalide este método para interrogar al servicio.|
|[CAtlServiceModuleT::OnPause](#onpause)|Invalide este método para pausar el servicio.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Invalide este método para cerrar el servicio|
|[CAtlServiceModuleT::OnStop](#onstop)|Invalide este método para detener el servicio|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Invalide este método para controlar las solicitudes desconocidas al servicio|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro si es necesario.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Se llama a este método inmediatamente antes de entrar en el bucle de mensajes.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registra el servicio en el registro.|
|[CAtlServiceModuleT::Run](#run)|Ejecuta el servicio.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Método al que llama el administrador de control de servicios.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Actualiza el estado del servicio.|
|[CAtlServiceModuleT::Start](#start)|Lo llama `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Detiene y quita el servicio.|
|[CAtlServiceModuleT::Unlock](#unlock)|Disminuye el recuento de bloqueos del servicio.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Quita el servicio del registro.|
|[CAtlServiceModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar el servicio.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Marca que indica que el programa se está ejecutando como un servicio.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Variable miembro que almacena el identificador del subproceso.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Variable miembro que almacena un identificador de la estructura de información de estado para el servicio actual.|
|[CAtlServiceModuleT::m_status](#m_status)|Variable de miembro que almacena la estructura de información de estado para el servicio actual.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Nombre del servicio que se va a registrar.|

## <a name="remarks"></a>Comentarios

`CAtlServiceModuleT`, derivado de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementa un módulo de servicio ATL. `CAtlServiceModuleT`proporciona métodos para el procesamiento, la instalación, el registro y la eliminación de la línea de comandos. Si se requiere una funcionalidad adicional, se pueden invalidar estos y otros métodos.

Esta clase reemplaza la clase de [CComModule](../../atl/reference/ccommodule-class.md) obsoleta utilizada en versiones anteriores de ATL. Vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

El constructor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa los miembros de datos y establece el estado del servicio inicial.

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

La rutina de controlador para el servicio.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Modificador que define la operación del controlador. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Este es el código al que llama el administrador de control de servicios (SCM) para recuperar el estado del servicio y emitir instrucciones como detener o pausar. El SCM pasa un código de operación, que se muestra `Handler` a continuación, a para indicar lo que debe hacer el servicio.

|Código de operación|Significado|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Detiene el servicio. Invalide el método [CAtlServiceModuleT:: OnStop](#onstop) en ATLBase. h para cambiar el comportamiento.|
|SERVICE_CONTROL_PAUSE|Implementado por el usuario. Invalide el método vacío [CAtlServiceModuleT:: OnPause](#onpause) en ATLBase. h para pausar el servicio.|
|SERVICE_CONTROL_CONTINUE|Implementado por el usuario. Invalide el método vacío [CAtlServiceModuleT:: OnContinue](#oncontinue) en ATLBase. h para continuar el servicio.|
|SERVICE_CONTROL_INTERROGATE|Implementado por el usuario. Invalide el método vacío [CAtlServiceModuleT::](#oninterrogate) alinterrogate en ATLBase. h para interrogar el servicio.|
|SERVICE_CONTROL_SHUTDOWN|Implementado por el usuario. Invalide el método vacío [CAtlServiceModuleT:: alshutdown](#onshutdown) en ATLBase. h para cerrar el servicio.|

Si no se reconoce el código de la operación, se llama al método [CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) .

Un servicio generado por ATL predeterminado solo controla la instrucción Stop. Si el SCM pasa la instrucción Stop, el servicio indica al SCM que el programa está a punto de detenerse. Después, el servicio `PostThreadMessage` llama a para enviar un mensaje de salida a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

Proporciona la configuración de seguridad predeterminada para el servicio.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Cualquier clase que derive de `CAtlServiceModuleT` debe implementar este método en la clase derivada.

Use la autenticación de nivel de PKT, el nivel de suplantación de RPC_C_IMP_LEVEL_IDENTIFY y un descriptor de seguridad no `CoInitializeSecurity`null adecuado en la llamada a.

En el caso de los proyectos de servicio sin atributos generados por el asistente, esto sería

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

En el caso de los proyectos de servicio con atributos, esto sería en

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

Instala y crea el servicio.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Instala el servicio en la base de datos del administrador de control de servicios (SCM) y, a continuación, crea el objeto de servicio. Si no se pudo crear el servicio, se muestra un cuadro de mensaje y el método devuelve FALSE.

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

Confirma que se ha instalado el servicio.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el servicio está instalado, FALSE en caso contrario.

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

Escribe en el registro de eventos.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena que se va a escribir en el registro de eventos.

*...*<br/>
Cadenas adicionales opcionales que se van a escribir en el registro de eventos.

### <a name="remarks"></a>Comentarios

Este método escribe detalles en un registro de eventos mediante la función [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Si no hay ningún servicio en ejecución, la cadena se envía a la consola.

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

Marca que indica que el programa se está ejecutando como un servicio.

```
BOOL m_bService;
```

### <a name="remarks"></a>Comentarios

Se usa para distinguir un archivo EXE de un archivo EXE de la aplicación.

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

Variable miembro que almacena el identificador de subproceso del servicio.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Comentarios

Esta variable almacena el identificador de subproceso del subproceso actual.

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

Variable miembro que almacena un identificador de la estructura de información de estado para el servicio actual.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Comentarios

La estructura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contiene información sobre un servicio.

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

Variable de miembro que almacena la estructura de información de estado para el servicio actual.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Comentarios

La estructura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) contiene información sobre un servicio.

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

Nombre del servicio que se va a registrar.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Comentarios

Una cadena terminada en null que almacena el nombre del servicio.

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

Invalide este método para continuar el servicio.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

Invalide este método para interrogar al servicio.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

Invalide este método para pausar el servicio.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

Invalide este método para cerrar el servicio.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

Invalide este método para detener el servicio.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

Invalide este método para controlar las solicitudes desconocidas al servicio.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Reservado.

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

Analiza la línea de comandos y realiza el registro si es necesario.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
Línea de comandos.

*pnRetCode*<br/>
HRESULT correspondiente al registro (si tuvo lugar).

### <a name="return-value"></a>Valor devuelto

Devuelve true si es correcto o false si no se pudo registrar el archivo RGS proporcionado en la línea de comandos.

### <a name="remarks"></a>Comentarios

Analiza la línea de comandos y registra o anula el registro del archivo RGS proporcionado si es necesario. Este método llama a [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline) para comprobar **/regserver** y **modificador/unregserver**. Al agregar el argumento **-/Service** , se registrará el servicio.

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

Se llama a este método inmediatamente antes de entrar en el bucle de mensajes.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Este parámetro se pasa a [CAtlExeModuleT::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Invalide este método para agregar código de inicialización personalizado para el servicio.

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

Registra el servicio en el registro.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parámetros

*bService*<br/>
Debe ser true para registrarse como servicio.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="run"></a>  CAtlServiceModuleT::Run

Ejecuta el servicio.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Después de llamar a `Run` , llama a [CAtlServiceModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)y [CAtlExeModuleT::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain

El administrador de control de servicios llama a este método.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parámetros

*dwArgc*<br/>
El argumento argc.

*lpszArgv*<br/>
El argumento argv.

### <a name="remarks"></a>Comentarios

El administrador de control de servicios (SCM `ServiceMain` ) llama al abrir la aplicación servicios en el panel de control, seleccione el servicio y haga clic en iniciar.

Una vez que el `ServiceMain`SCM llama a, un servicio debe proporcionar al SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (como pausar o detener). Posteriormente, se llama a [CAtlServiceModuleT:: Run](#run) para realizar el trabajo principal del servicio. `Run`continúa ejecutándose hasta que se detiene el servicio.

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

Este método actualiza el estado del servicio.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parámetros

*dwState*<br/>
Nuevo estado. Consulte [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) para ver los valores posibles.

### <a name="remarks"></a>Comentarios

Actualiza la información de estado del administrador de control de servicios para el servicio. Lo llama [CAtlServiceModuleT:: Run](#run), [CAtlServiceModuleT:: ServiceMain](#servicemain) y otros métodos de controlador. El estado también se almacena en la variable miembro [CAtlServiceModuleT:: m_status](#m_status).

##  <a name="start"></a>  CAtlServiceModuleT::Start

Lo llama `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El método [CAtlServiceModuleT:: WinMain](#winmain) controla el registro y la instalación, así como las tareas implicadas en la eliminación de entradas del registro y en la desinstalación del módulo. Cuando se ejecuta el servicio, `WinMain` llama `Start`a.

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

Detiene y quita el servicio.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Detiene la ejecución del servicio y lo quita de la base de datos del administrador de control de servicios.

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

Disminuye el recuento de bloqueos del servicio.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el recuento de bloqueos, que puede ser útil para los diagnósticos y la depuración.

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

Quita el servicio del registro.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

Este método implementa el código necesario para iniciar el servicio.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la sección [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del servicio.

### <a name="remarks"></a>Comentarios

Este método procesa la línea de comandos (con [CAtlServiceModuleT::P arsecommandline](#parsecommandline)) y, a continuación, inicia el servicio (mediante [CAtlServiceModuleT:: Start](#start)).

## <a name="see-also"></a>Vea también

[CAtlExeModuleT (clase)](../../atl/reference/catlexemodulet-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
