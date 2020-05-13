---
title: COleObjectFactory (clase)
ms.date: 11/04/2016
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
ms.openlocfilehash: 165ba7c1918c3ccc5d5d7e0bc067fba86678a3e7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753805"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (clase)

Implementa el generador de clases OLE, que crea objetos OLE tales como servidores, objetos de automatización y documentos.

## <a name="syntax"></a>Sintaxis

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construye un objeto `COleObjectFactory`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Devuelve el identificador de clase OLE de los objetos que crea este generador.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Determina si la licencia del control es válida.|
|[COleObjectFactory::IsRegistered](#isregistered)|Indica si el generador de objetos está registrado con los archivos DLL del sistema OLE.|
|[COleObjectFactory::Register](#register)|Registra este generador de objetos con los archivos DLL del sistema OLE.|
|[COleObjectFactory::RegisterAll](#registerall)|Registra todos los generadores de objetos de la aplicación con archivos DLL del sistema OLE.|
|[COleObjectFactory::Revoke](#revoke)|Revoca el registro de este generador de objetos con los archivos DLL del sistema OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Revoca los registros de los generadores de objetos de una aplicación con los archivos DLL del sistema OLE.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Anula el registro de todos los generadores de objetos de una aplicación.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registra este generador de objetos con el registro del sistema OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Solicita una clave única del archivo DLL del control.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Llamado por el marco de trabajo para crear un nuevo objeto del tipo de esta fábrica.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Comprueba que la clave incrustada en el control coincide con la clave incrustada en el contenedor.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Comprueba que el control tiene licencia para su uso en tiempo de diseño.|

## <a name="remarks"></a>Observaciones

La `COleObjectFactory` clase tiene funciones miembro para realizar las siguientes funciones:

- Gestión del registro de objetos.

- Actualización del registro del sistema OLE, así como el registro en tiempo de ejecución que informa a OLE de que los objetos se están ejecutando y listos para recibir mensajes.

- Hacer cumplir las licencias limitando el uso del control a los desarrolladores con licencia en tiempo de diseño y a las aplicaciones con licencia en tiempo de ejecución.

- Registro de generadores de objetos de control con el registro del sistema OLE.

Para obtener más información acerca de la creación de objetos, vea los artículos Objetos de datos y orígenes de [datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md) y Objetos de datos y orígenes de [datos: Creación y destrucción](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Para obtener más información sobre el registro, consulte el artículo [Registro](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory

Construye un `COleObjectFactory` objeto, lo inicializa como un generador de objetos no registrado y lo agrega a la lista de generadores.

```
COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    LPCTSTR lpszProgID);

COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    int nFlags,
    LPCTSTR lpszProgID);
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
Referencia al identificador de clase OLE que representa este generador de objetos.

*pRuntimeClass*<br/>
Puntero a la clase en tiempo de ejecución de los objetos C++ que puede crear esta fábrica.

*bMultiInstance*<br/>
Indica si una sola instancia de la aplicación puede admitir varias instancias. Si es TRUE, se inician varias instancias de la aplicación para cada solicitud para crear un objeto.

*nFlags*<br/>
Contiene uno o varios de los siguientes indicadores:

- `afxRegDefault`Establece el modelo de subprocesamiento en ThreadingModel-Apartment.

- `afxRegInsertable`Permite que el control aparezca en el cuadro de diálogo **Insertar objeto** para objetos OLE.

- `afxRegApartmentThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Apartment.

- `afxRegFreeThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Free.

   Puede combinar los `afxRegApartmentThreading` dos `afxRegFreeThreading` indicadores y establecer ThreadingModel-Both. Consulte [InprocServer32](/windows/win32/com/inprocserver32) en el Windows SDK para obtener más información sobre el registro del modelo de subprocesos.

*lpszProgID*<br/>
Puntero a una cadena que contiene un identificador de programa verbal, como "Microsoft Excel."

### <a name="remarks"></a>Observaciones

Para utilizar el objeto, sin embargo, debe registrarlo.

Para obtener más información, consulte [Clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID

Devuelve una referencia al identificador de clase OLE que representa este generador.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al identificador de clase OLE que representa este generador.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey

Solicita una clave de licencia única del archivo DLL del control y la almacena en el BSTR al que apunta *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para uso futuro.

*pbstrKey*<br/>
Puntero a un BSTR que almacenará la clave de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena de clave de licencia no es NULL; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función devuelve 0 y no almacena nada en el BSTR. Si usa MFC ActiveX ControlWizard para crear el proyecto, ControlWizard proporciona una invalidación que recupera la clave de licencia del control.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid

Determina si la licencia del control es válida.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valor devuelto

TRUESi successul; de lo contrario falso.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::IsRegistered

Devuelve un valor distinto de cero si el generador está registrado con los archivos DLL del sistema OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fábrica está registrada; de lo contrario 0.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject

Llamado por el marco de trabajo para crear un nuevo objeto.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto creado. Puede producir una excepción de memoria si se produce un error.

### <a name="remarks"></a>Observaciones

Invalide esta función para crear el objeto a partir de algo distinto de la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pasado al constructor.

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Register

Registra este generador de objetos con los archivos DLL del sistema OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fábrica se ha registrado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) llama a esta función cuando se inicia la aplicación.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll

Registra todos los generadores de objetos de la aplicación con los archivos DLL del sistema OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las fábricas se registran correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) llama a esta función cuando se inicia la aplicación.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Revoke

Revoca el registro de este generador de objetos con los archivos DLL del sistema OLE.

```cpp
void Revoke();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, llámelo desde una invalidación de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::RevokeAll

Revoca todos los registros de fábricas de objetos de la aplicación con los archivos DLL del sistema OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, llámelo desde una invalidación de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::UnregisterAll

Anula el registro de todos los generadores de objetos de una aplicación.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::UpdateRegistry

Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.

```cpp
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parámetros

*lpszProgID*<br/>
Puntero a una cadena que contiene el identificador de programa legible por el usuario, como "Excel.Document.5."

*bRegistro*<br/>
Determina si se va a registrar el generador de objetos de la clase de control.

### <a name="remarks"></a>Observaciones

A continuación se describen breves los dos formularios para esta función:

- **UpdateRegistry(** `lpszProgID` **)** Registra este generador de objetos con el registro del sistema OLE. Normalmente, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) llama a esta función cuando se inicia la aplicación.

- **UpdateRegistry(** `bRegister` **)** Esta forma de la función es reemplazable. Si *bRegister* es TRUE, esta función registra la clase de control con el registro del sistema. De lo contrario, anula el registro de la clase.

   Si usa MFC ActiveX ControlWizard para crear el proyecto, ControlWizard proporciona una invalidación a esta función virtual pura.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll

Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parámetros

*bRegistro*<br/>
Determina si se va a registrar el generador de objetos de la clase de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las fábricas se actualizan correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) llama a esta función cuando se inicia la aplicación.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey

Comprueba que el contenedor tiene licencia para usar el control OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parámetros

*bstrKey*<br/>
Un BSTR que almacena la versión del contenedor de la cadena de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia en tiempo de ejecución es válida; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La versión predeterminada llama a [GetLicenseKey](#getlicensekey) para obtener una copia de la cadena de licencia del control y la compara con la cadena en *bstrKey*. Si las dos cadenas coinciden, la función devuelve un valor distinto de cero; de lo contrario devuelve 0.

Puede invalidar esta función para proporcionar una verificación personalizada de la licencia.

La función [VerifyUserLicense](#verifyuserlicense) comprueba la licencia en tiempo de diseño.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense

Comprueba la licencia en tiempo de diseño para el control OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia en tiempo de diseño es válida; de lo contrario 0.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
