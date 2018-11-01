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
ms.openlocfilehash: 4aa6d688de59884c7279b441d12dda9dcdf2ff6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476016"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (clase)

Implementa el generador de clases OLE, que crea objetos OLE tales como servidores, objetos de automatización y documentos.

## <a name="syntax"></a>Sintaxis

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construye un objeto `COleObjectFactory`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Devuelve la OLE identificador de clase de los objetos que crea este generador.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Determina si la licencia del control es válida.|
|[COleObjectFactory::IsRegistered](#isregistered)|Indica si el generador de objetos está registrado con la DLL del sistema OLE.|
|[COleObjectFactory::Register](#register)|Registra este generador de objetos con la DLL del sistema OLE.|
|[COleObjectFactory:: RegisterAll](#registerall)|Registra todos los generadores de objetos de la aplicación con la DLL del sistema OLE.|
|[COleObjectFactory::Revoke](#revoke)|Revoca el registro del generador de este objeto con la DLL del sistema OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Revoca los registros de las fábricas de objeto de la aplicación con la DLL del sistema OLE.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Anula el registro de todos los generadores de objetos de la aplicación.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Registra este generador de objetos con el registro del sistema OLE.|
|[COleObjectFactory:: UpdateRegistryAll](#updateregistryall)|Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Solicita una clave única de la DLL del control.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Lo llama el marco para crear un nuevo objeto de tipo de este generador.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Comprueba que la clave insertada en el control coincide con la clave insertada en el contenedor.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Comprueba que el control tiene licencia para uso en tiempo de diseño.|

## <a name="remarks"></a>Comentarios

La `COleObjectFactory` clase tiene funciones de miembro para llevar a cabo las siguientes funciones:

- Administrar el registro de objetos.

- Actualizando el registro del sistema OLE, así como el registro de tiempo de ejecución que le informa de OLE que los objetos se están ejecutando y está listo para recibir mensajes.

- Aplicación de licencias mediante la limitación de uso del control para los desarrolladores con licencia en tiempo de diseño y a las aplicaciones con licencia en tiempo de ejecución.

- Registrar generadores de objeto de control con el registro del sistema OLE.

Para obtener más información sobre la creación de objetos, consulte los artículos [objetos de datos y orígenes de datos (OLE)](../../mfc/data-objects-and-data-sources-ole.md) y [objetos de datos y orígenes de datos: creación y destrucción](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Para obtener más información acerca del registro, consulte el artículo [registro](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

Construye un `COleObjectFactory` objeto, lo inicializa como un generador de objetos no registrados y lo agrega a la lista de fábricas.

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

*CLSID*<br/>
Referencia a este generador de objetos representa el identificador de clase OLE.

*pRuntimeClass*<br/>
Puntero a la clase de tiempo de ejecución de los objetos de C++, que puede crear este generador.

*bMultiInstance al*<br/>
Indica si una sola instancia de la aplicación puede admitir varias creaciones de instancias. Si es TRUE, se inician múltiples instancias de la aplicación para que cada solicitud crear un objeto.

*nFlags*<br/>
Contiene uno o varios de los siguientes indicadores:

- `afxRegDefault` Establece el modelo de subprocesos para ThreadingModel = apartamento.

- `afxRegInsertable` Permite que el control aparezca en el **Insertar objeto** cuadro de diálogo para los objetos OLE.

- `afxRegApartmentThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.

- `afxRegFreeThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = gratis.

   Puede combinar las dos marcas `afxRegApartmentThreading` y `afxRegFreeThreading` establecer ThreadingModel = Both. Consulte [InprocServer32](/windows/desktop/com/inprocserver32) en el SDK de Windows para obtener más información sobre el registro del modelo de subprocesos.

*lpszProgID*<br/>
Puntero a una cadena que contiene un identificador de programa verbales, como "Microsoft Excel."

### <a name="remarks"></a>Comentarios

Para usar el objeto, sin embargo, debe registrarlo.

Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) en el SDK de Windows.

##  <a name="getclassid"></a>  COleObjectFactory::GetClassID

Devuelve una referencia al identificador de clase OLE representa esta factoría.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Representa la referencia al identificador de clase OLE este generador.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) en el SDK de Windows.

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

Solicita una clave de licencia única del archivo DLL del control y lo almacena en el BSTR apuntado *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parámetros

*dwReservado*<br/>
Reservado para un uso futuro.

*pbstrKey*<br/>
Puntero a un valor BSTR que se almacenará la clave de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena de clave de licencia no es NULL; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función devuelve 0 y no almacena nada en BSTR. Si usas ActiveX ControlWizard de MFC para crear el proyecto, ControlWizard proporciona una invalidación que recupera la clave de licencia del control.

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

Determina si la licencia del control es válida.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valor devuelto

TRUE si realizado correctamente; en caso contrario, false.

##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered

Devuelve un valor distinto de cero si el generador se registra con la DLL del sistema OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el generador se registra; en caso contrario, es 0.

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

Lo llama el marco para crear un nuevo objeto.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto creado. Puede producir una excepción de memoria si se produce un error.

### <a name="remarks"></a>Comentarios

Reemplace esta función para crear el objeto desde algo distinto de la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pasado al constructor.

##  <a name="register"></a>  COleObjectFactory::Register

Registra este generador de objetos con la DLL del sistema OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha registrado correctamente el generador; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="registerall"></a>  COleObjectFactory:: RegisterAll

Registra todos los generadores de objetos de la aplicación con la DLL del sistema OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha registrado correctamente las fábricas; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="revoke"></a>  COleObjectFactory::Revoke

Revoca el registro del generador de este objeto con la DLL del sistema OLE.

```
void Revoke();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función automáticamente antes de que termine la aplicación. Si es necesario, puede llamarlo desde un reemplazo de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

Revoca todos los registros de las fábricas de objeto de la aplicación con la DLL del sistema OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función automáticamente antes de que termine la aplicación. Si es necesario, puede llamarlo desde un reemplazo de [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

Anula el registro de todos los generadores de objetos de la aplicación.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry

Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parámetros

*lpszProgID*<br/>
Puntero a una cadena que contiene el identificador de programa de lenguaje natural, por ejemplo, "Excel.Document.5".

*bInscríbase al*<br/>
Determina si el generador de objetos de la clase de control es que se registrarán.

### <a name="remarks"></a>Comentarios

Siguen las discusiones breves de las dos formas para esta función:

- **UpdateRegistry (** `lpszProgID` **)** registra este generador de objetos con el registro del sistema OLE. Esta función normalmente se llama mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

- **UpdateRegistry (** `bRegister` **)** esta forma de la función es reemplazable. Si *bInscríbase al* es TRUE, este registros de función, el control de clases con el registro del sistema. En caso contrario, anula el registro de la clase.

   Si usas ActiveX ControlWizard de MFC para crear el proyecto, ControlWizard proporciona una invalidación para esta función virtual pura.

##  <a name="updateregistryall"></a>  COleObjectFactory:: UpdateRegistryAll

Registra todos los generadores de objetos de la aplicación con el registro del sistema OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parámetros

*bInscríbase al*<br/>
Determina si el generador de objetos de la clase de control es que se registrarán.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha actualizado correctamente las fábricas; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama mediante [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) cuando se inicia la aplicación.

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

Comprueba que el contenedor tiene licencia para usar el control OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parámetros

*bstrKey*<br/>
Una cadena BSTR almacenar la versión del contenedor de la cadena de licencia.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia de tiempo de ejecución es válida; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La versión predeterminada llama [GetLicenseKey](#getlicensekey) para obtener una copia del control de la cadena de licencia y lo compara con la cadena en *bstrKey*. Si las dos cadenas coinciden, la función devuelve un valor distinto de cero; en caso contrario, devuelve 0.

Puede reemplazar esta función para proporcionar una verificación personalizada de la licencia.

La función [VerifyUserLicense](#verifyuserlicense) comprueba la licencia en tiempo de diseño.

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

Comprueba la licencia en tiempo de diseño para el control OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la licencia en tiempo de diseño es válida; en caso contrario, es 0.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
