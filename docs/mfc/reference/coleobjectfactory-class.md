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
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503735"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (clase)

Implementa el generador de clases OLE, que crea objetos OLE tales como servidores, objetos de automatización y documentos.

## <a name="syntax"></a>Sintaxis

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construye un objeto `COleObjectFactory`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Devuelve el identificador de clase OLE de los objetos que este generador crea.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Determina si la licencia del control es válida.|
|[COleObjectFactory::IsRegistered](#isregistered)|Indica si el generador de objetos está registrado con los archivos DLL del sistema OLE.|
|[COleObjectFactory::Register](#register)|Registra este generador de objetos con los archivos DLL del sistema OLE.|
|[COleObjectFactory::RegisterAll](#registerall)|Registra todos los generadores de objetos de la aplicación con archivos DLL del sistema OLE.|
|[COleObjectFactory::Revoke](#revoke)|Revoca el registro de este generador de objetos con los archivos DLL del sistema OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Revoca los registros de los generadores de objetos de una aplicación con los archivos DLL del sistema OLE.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Anula el registro de todos los generadores de objetos de una aplicación.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registra este generador de objetos en el registro del sistema OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Registra todos los generadores de objetos de la aplicación en el registro del sistema OLE.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Solicita una clave única a la DLL del control.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Lo llama el marco de trabajo para crear un nuevo objeto de tipo de generador.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Comprueba que la clave incrustada en el control coincide con la clave incrustada en el contenedor.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Comprueba que el control tiene licencia para su uso en tiempo de diseño.|

## <a name="remarks"></a>Comentarios

La `COleObjectFactory` clase tiene funciones miembro para realizar las funciones siguientes:

- Administrar el registro de objetos.

- Actualizar el registro del sistema OLE, así como el registro en tiempo de ejecución que informa a OLE de que los objetos se están ejecutando y están listos para recibir mensajes.

- Aplicar las licencias limitando el uso del control a los desarrolladores con licencia en tiempo de diseño y a las aplicaciones con licencia en tiempo de ejecución.

- Registrando generadores de objetos de control con el registro del sistema OLE.

Para obtener más información acerca de la creación de objetos, vea los artículos [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md) y [objetos de datos y orígenes de datos: Creación y destrucción](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Para obtener más información sobre el registro, consulte el artículo [registro](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

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
Referencia al identificador de clase OLE que este generador de objetos representa.

*pRuntimeClass*<br/>
Puntero a la clase en tiempo de ejecución de C++ los objetos que este generador puede crear.

*bMultiInstance*<br/>
Indica si una única instancia de la aplicación puede admitir varias creaciones de instancias. Si es TRUE, se inician varias instancias de la aplicación para cada solicitud de creación de un objeto.

*nFlags*<br/>
Contiene una o varias de las marcas siguientes:

- `afxRegDefault`Establece el modelo de subprocesos en ThreadingModel = Apartment.

- `afxRegInsertable`Permite que el control aparezca en el cuadro de diálogo **Insertar objeto** para los objetos OLE.

- `afxRegApartmentThreading`Establece el modelo de subprocesos del registro en ThreadingModel = Apartment.

- `afxRegFreeThreading`Establece el modelo de subprocesos del registro en ThreadingModel = Free.

   Puede combinar las dos marcas `afxRegApartmentThreading` y `afxRegFreeThreading` establecer ThreadingModel = both. Consulte [InProcServer32](/windows/win32/com/inprocserver32) en el Windows SDK para obtener más información sobre el registro del modelo de subprocesos.

*lpszProgID*<br/>
Puntero a una cadena que contiene un identificador de programa verbal, como "Microsoft Excel".

### <a name="remarks"></a>Comentarios

Sin embargo, para usar el objeto, debe registrarlo.

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

##  <a name="getclassid"></a>  COleObjectFactory::GetClassID

Devuelve una referencia al identificador de clase OLE que este generador representa.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al identificador de clase OLE que este generador representa.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

Solicita una clave de licencia única del archivo DLL del control y la almacena en el BSTR al que apunta *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para un uso futuro.

*pbstrKey*<br/>
Puntero a un BSTR que almacenará la clave de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena de clave de licencia no es NULL; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función devuelve 0 y no almacena nada en el BSTR. Si utiliza ControlWizard ActiveX MFC para crear el proyecto, ControlWizard proporciona una invalidación que recupera la clave de licencia del control.

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

Determina si la licencia del control es válida.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valor devuelto

TRUE si successul; en caso contrario, false.

##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered

Devuelve un valor distinto de cero si el generador se registra con los archivos DLL del sistema OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador está registrado; de lo contrario, es 0.

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

Lo llama el marco de trabajo para crear un nuevo objeto.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto creado. Puede producir una excepción de memoria si se produce un error.

### <a name="remarks"></a>Comentarios

Invalide esta función para crear el objeto a partir de un elemento que no sea el objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pasado al constructor.

##  <a name="register"></a>  COleObjectFactory::Register

Registra este generador de objetos con los archivos DLL del sistema OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador se ha registrado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a esta función normalmente se realiza mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

Registra todos los generadores de objetos de la aplicación con los archivos DLL del sistema OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los generadores se registran correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a esta función normalmente se realiza mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="revoke"></a>  COleObjectFactory::Revoke

Revoca el registro de este generador de objetos con los archivos DLL del sistema OLE.

```
void Revoke();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, llámelo desde una invalidación de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

Revoca todos los registros de los generadores de objetos de la aplicación con los archivos DLL del sistema OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función automáticamente antes de que finalice la aplicación. Si es necesario, llámelo desde una invalidación de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

Anula el registro de todos los generadores de objetos de una aplicación.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry

Registra todos los generadores de objetos de la aplicación en el registro del sistema OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parámetros

*lpszProgID*<br/>
Puntero a una cadena que contiene el identificador de programa legible, como "Excel. Document. 5".

*bRegister*<br/>
Determina si el generador de objetos de la clase de control se va a registrar.

### <a name="remarks"></a>Comentarios

Las discusiones breves de las dos formas para esta función son:

- **UpdateRegistry (** `lpszProgID` **)** registra este generador de objetos en el registro del sistema OLE. La llamada a esta función normalmente se realiza mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

- **UpdateRegistry (** `bRegister` **)** esta forma de la función es reemplazable. Si *bRegister* es true, esta función registra la clase de control con el registro del sistema. De lo contrario, anula el registro de la clase.

   Si usa ActiveX de MFC ControlWizard para crear el proyecto, ControlWizard proporciona una invalidación a esta función virtual pura.

##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll

Registra todos los generadores de objetos de la aplicación en el registro del sistema OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parámetros

*bRegister*<br/>
Determina si el generador de objetos de la clase de control se va a registrar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los generadores se actualizan correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a esta función normalmente se realiza mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

Comprueba que el contenedor tiene licencia para usar el control OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parámetros

*bstrKey*<br/>
BSTR que almacena la versión del contenedor de la cadena de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia en tiempo de ejecución es válida; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La versión predeterminada llama a [GetLicenseKey](#getlicensekey) para obtener una copia de la cadena de licencia del control y la compara con la cadena de *bstrKey*. Si las dos cadenas coinciden, la función devuelve un valor distinto de cero; en caso contrario, devuelve 0.

Puede invalidar esta función para proporcionar una comprobación personalizada de la licencia.

La función [VerifyUserLicense](#verifyuserlicense) comprueba la licencia en tiempo de diseño.

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

Comprueba la licencia en tiempo de diseño para el control OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia en tiempo de diseño es válida; de lo contrario, es 0.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
