---
title: CAtlServiceModuleT (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 2d4d5d4a5c4d8a52f792cc04a968974967c1e13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260206"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT (clase)

Esta clase implementa un servicio.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CAtlServiceModuleT`.

*nServiceNameID*<br/>
El identificador de recurso del servicio.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|La rutina del controlador para el servicio.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Proporciona el valor predeterminado de configuración de seguridad para el servicio.|
|[CAtlServiceModuleT::Install](#install)|Instala y crea el servicio.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Confirma que se ha instalado el servicio.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Escribe en el registro de eventos.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Invalide este método para continuar el servicio.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Invalide este método para consultar el servicio.|
|[CAtlServiceModuleT::OnPause](#onpause)|Invalide este método para poner en pausa el servicio.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Invalide este método para cerrar el servicio|
|[CAtlServiceModuleT::OnStop](#onstop)|Invalide este método para detener el servicio|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Invalide este método para controlar solicitudes desconocidas para el servicio|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro, si es necesario.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Este método se llama inmediatamente antes de entrar en el bucle de mensajes.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registra el servicio en el registro.|
|[CAtlServiceModuleT::Run](#run)|Ejecuta el servicio.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|El método llamado por el Administrador de Control de servicios.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Actualiza el estado del servicio.|
|[CAtlServiceModuleT::Start](#start)|Lo llama `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Detiene y elimina el servicio.|
|[CAtlServiceModuleT::Unlock](#unlock)|Disminuye el recuento de bloqueo del servicio.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Quita el servicio del registro.|
|[CAtlServiceModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar el servicio.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Marca que indica que el programa se ejecuta como un servicio.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Variable miembro almacena el identificador de subproceso.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Almacenar un identificador de la estructura de información de estado del servicio actual de la variable de miembro.|
|[CAtlServiceModuleT::m_status](#m_status)|Almacenar la estructura de información de estado del servicio actual de la variable de miembro.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|El nombre del servicio que se está registrando.|

## <a name="remarks"></a>Comentarios

`CAtlServiceModuleT`, derivado de [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementa un módulo de servicio de ATL. `CAtlServiceModuleT` Proporciona métodos para el procesamiento de línea de comandos, instalación, registro y eliminación. Si se requiere una funcionalidad adicional, se pueden invalidar estos y otros métodos.

Esta clase reemplaza el atributo obsolete [CComModule (clase)](../../atl/reference/ccommodule-class.md) usado en versiones anteriores de ATL. Consulte [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

El constructor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa a los miembros de datos y establece el estado del servicio inicial.

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

La rutina del controlador para el servicio.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Un conmutador que define la operación del controlador. Para obtener más información, vea los comentarios.

### <a name="remarks"></a>Comentarios

Este es el código que llama el Administrador de Control de servicios (SCM) para recuperar el estado de las instrucciones de servicio y emitir, como detener o pausar. El SCM pasa un código de operación, se muestra a continuación, al `Handler` para indicar lo que debe hacer el servicio.

|Código de operación|Significado|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Detiene el servicio. Invalide el método [CAtlServiceModuleT::OnStop](#onstop) en atlbase.h para cambiar el comportamiento.|
|SERVICE_CONTROL_PAUSE|Implementa el usuario. Invalidar el método vacío [CAtlServiceModuleT::OnPause](#onpause) en atlbase.h para pausar el servicio.|
|SERVICE_CONTROL_CONTINUE|Implementa el usuario. Invalidar el método vacío [CAtlServiceModuleT::OnContinue](#oncontinue) en atlbase.h para continuar el servicio.|
|SERVICE_CONTROL_INTERROGATE|Implementa el usuario. Invalidar el método vacío [CAtlServiceModuleT::OnInterrogate](#oninterrogate) en atlbase.h al consultar el servicio.|
|SERVICE_CONTROL_SHUTDOWN|Implementa el usuario. Invalidar el método vacío [CAtlServiceModuleT::OnShutdown](#onshutdown) en atlbase.h para apagar el servicio.|

Si no se reconoce el código de operación, el método [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) se llama.

Servicio predeterminado generado por ATL sólo controla la instrucción stop. Si el SCM pasa dicha instrucción, el servicio indica el SCM que el programa está a punto de detenerse. El servicio, a continuación, llama a `PostThreadMessage` para publicar un mensaje a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

Proporciona el valor predeterminado de configuración de seguridad para el servicio.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

En Visual Studio .NET 2003, este método no se implementa en la clase base. El Asistente para proyectos de Visual Studio incluye este método en el código generado, pero se producirá un error de compilación si se compila un proyecto creado en una versión anterior de Visual C++ mediante ATL 7.1. Cualquier clase que derive de `CAtlServiceModuleT` debe implementar este método en la clase derivada.

Usar autenticación de nivel PKT, nivel de suplantación de RPC_C_IMP_LEVEL_IDENTIFY y un descriptor de seguridad de no null apropiado en la llamada a `CoInitializeSecurity`.

Para proyectos de servicio sin atributos generados por el asistente, esto sería en

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Para proyectos de servicio con atributos, esto sería en

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

Instala y crea el servicio.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Instala el servicio en la base de datos de administrador de Control de servicios (SCM) y, a continuación, crea el objeto de servicio. Si no se pudo crear el servicio, se muestra un cuadro de mensaje y el método devuelve FALSE.

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
Cadenas adicionales opcionales se escriban en el registro de eventos.

### <a name="remarks"></a>Comentarios

Este método escribe los detalles en un registro de eventos mediante la función [ReportEvent](/windows/desktop/api/winbase/nf-winbase-reporteventa). Si no se está ejecutando ningún servicio, la cadena se envía a la consola.

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

Marca que indica que el programa se ejecuta como un servicio.

```
BOOL m_bService;
```

### <a name="remarks"></a>Comentarios

Se usa para distinguir un servicio EXE desde un archivo EXE de la aplicación.

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

Variable miembro almacena el identificador de subproceso del servicio.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Comentarios

Esta variable almacena el identificador de subproceso del subproceso actual.

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

Almacenar un identificador de la estructura de información de estado del servicio actual de la variable de miembro.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Comentarios

El [SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) estructura contiene información acerca de un servicio.

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

Almacenar la estructura de información de estado del servicio actual de la variable de miembro.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Comentarios

El [SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) estructura contiene información acerca de un servicio.

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

El nombre del servicio que se está registrando.

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

Invalide este método para consultar el servicio.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

Invalide este método para poner en pausa el servicio.

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

Invalide este método para controlar solicitudes desconocidas para el servicio.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parámetros

*dwOpcode*<br/>
Reservado.

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

Analiza la línea de comandos y realiza el registro, si es necesario.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parámetros

*lpCmdLine*<br/>
Línea de comandos.

*pnRetCode*<br/>
HRESULT correspondiente al registro (si se llevó a cabo).

### <a name="return-value"></a>Valor devuelto

Devuelve true si funciona correctamente o falso si no se pudo registrar el archivo RGS proporcionado en la línea de comandos.

### <a name="remarks"></a>Comentarios

Analiza la línea de comandos y se registra o anula el registro el archivo RGS proporcionado si es necesario. Este método llama a [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) busque **/regserver** y **/UnregServer**. Agregar el argumento **- / servicio** registrará el servicio.

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

Este método se llama inmediatamente antes de entrar en el bucle de mensajes.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Este parámetro se pasa a [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Invalide este método para agregar código de inicialización personalizado para el servicio.

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

Registra el servicio en el registro.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parámetros

*bService*<br/>
Debe ser true para registrar como un servicio.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

##  <a name="run"></a>  CAtlServiceModuleT::Run

Ejecuta el servicio.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sección. El valor predeterminado es SW_HIDE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Después de que se llama, `Run` llamadas [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), y [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain

Este método se llama por el Administrador de Control de servicios.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parámetros

*dwArgc*<br/>
El argumento argc.

*lpszArgv*<br/>
El argumento argv.

### <a name="remarks"></a>Comentarios

Las llamadas del Administrador de Control de servicios (SCM) `ServiceMain` al abrir la aplicación de servicios en el Panel de Control, seleccione el servicio y haga clic en Inicio.

Después de la SCM llama `ServiceMain`, un servicio debe darle el SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (por ejemplo, pausar o detener). Posteriormente, [CAtlServiceModuleT:: Run](#run) se llama para realizar el trabajo principal del servicio. `Run` continúa ejecutándose hasta que el servicio está detenido.

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

Este método actualiza el estado del servicio.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parámetros

*dwState*<br/>
El estado nueva. Consulte [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) para los valores posibles.

### <a name="remarks"></a>Comentarios

Actualiza la información de estado del Administrador de Control de servicio para el servicio. Lo llama [CAtlServiceModuleT:: Run](#run), [CAtlServiceModuleT:: ServiceMain](#servicemain) y otros métodos de controlador. El estado también se almacena en la variable miembro [CAtlServiceModuleT::m_status](#m_status).

##  <a name="start"></a>  CAtlServiceModuleT::Start

Lo llama `CAtlServiceModuleT::WinMain` cuando se inicia el servicio.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sección.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El [a CAtlServiceModuleT:: WinMain](#winmain) método controla el registro y la instalación, así como las tareas relacionadas con la eliminación de entradas del registro y desinstalar el módulo. Cuando se ejecuta el servicio, `WinMain` llamadas `Start`.

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

Detiene y elimina el servicio.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Detiene la ejecución del servicio y lo quita de la base de datos de administrador de Control de servicio.

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

Disminuye el recuento de bloqueo del servicio.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el recuento de bloqueos, que puede ser útil para el diagnóstico y depuración.

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

Quita el servicio del registro.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

Este método implementa el código necesario para iniciar el servicio.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parámetros

*nShowCmd*<br/>
Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sección.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor devuelto del servicio.

### <a name="remarks"></a>Comentarios

Este método procesa la línea de comandos (con [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) y, a continuación, inicia el servicio (mediante [CAtlServiceModuleT:: Start](#start)).

## <a name="see-also"></a>Vea también

[CAtlExeModuleT (clase)](../../atl/reference/catlexemodulet-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
