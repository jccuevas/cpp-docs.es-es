---
title: Registrar controles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426202"
---
# <a name="registering-ole-controls"></a>Registrar controles OLE

Otras aplicaciones compatibles con OLE pueden tener acceso a los controles OLE, como otros objetos de servidor OLE. Esto se logra registrando la biblioteca de tipos y la clase del control.

Las funciones siguientes permiten agregar y quitar la clase, las páginas de propiedades y la biblioteca de tipos del control en la base de datos de registro de Windows:

### <a name="registering-ole-controls"></a>Registrar controles OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Agrega la clase del control a la base de datos de registro.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Agrega una página de propiedades de control a la base de datos de registro.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Agrega la biblioteca de tipos del control a la base de datos de registro.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Quita una clase de control o una clase de página de propiedades de la base de datos de registro.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Quita la biblioteca de tipos del control de la base de datos de registro.|

normalmente se llama a `AfxOleRegisterTypeLib` en la implementación de `DllRegisterServer`de un archivo DLL de control. De forma similar, `DllUnregisterServer`llama a `AfxOleUnregisterTypeLib`. la función miembro `UpdateRegistry` de una página de propiedades o generador de clases de un control suele llamar a `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`y `AfxOleUnregisterClass`.

##  <a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Registra la clase de control con la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de instancia del módulo asociado a la clase de control.

*CLSID*<br/>
IDENTIFICADOR de clase único del control.

*pszProgID*<br/>
IDENTIFICADOR del programa único del control.

*idTypeName*<br/>
IDENTIFICADOR de recurso de la cadena que contiene un nombre de tipo legible por el usuario para el control.

*idBitmap*<br/>
IDENTIFICADOR de recurso del mapa de bits utilizado para representar el control OLE en una barra de herramientas o paleta.

*nRegFlags*<br/>
Contiene una o varias de las marcas siguientes:

- `afxRegInsertable` permite que el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.

- `afxRegApartmentThreading` establece el modelo de subprocesos del registro en ThreadingModel = Apartment.

- `afxRegFreeThreading` establece el modelo de subprocesos del registro en ThreadingModel = Free.

   Puede combinar las dos marcas `afxRegApartmentThreading` y `afxRegFreeThreading` para establecer ThreadingModel = both. Consulte [InProcServer32](/windows/win32/com/inprocserver32) en el Windows SDK para obtener más información sobre el registro del modelo de subprocesos.

> [!NOTE]
>  En las versiones de MFC anteriores a MFC 4,2, el parámetro **int** *nRegFlags* era un parámetro bool, *bInsertable*, que permitía o no que se insertara el control desde el cuadro de diálogo Insertar objeto.

*dwMiscStatus*<br/>
Contiene una o varias de las siguientes marcas de estado (para obtener una descripción de las marcas, consulte enumeración OLEMISC en el Windows SDK):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
IDENTIFICADOR único de la clase del control.

*wVerMajor*<br/>
Número de versión principal de la clase de control.

*wVerMinor*<br/>
Número de versión secundaria de la clase de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la clase de control se registró; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esto permite que los contenedores que reconocen el control OLE utilicen el control. `AfxOleRegisterControlClass` actualiza el registro con el nombre y la ubicación del control en el sistema y también establece el modelo de subprocesos que el control admite en el registro. Para obtener más información, vea la [Nota técnica 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "subprocesamiento de modelo Apartamento en controles OLE" y [acerca de los procesos y subprocesos](/windows/win32/ProcThread/about-processes-and-threads) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

En el ejemplo anterior se muestra cómo se llama a `AfxOleRegisterControlClass` con la marca para insertarse y la marca del modelo de Apartamento ORed conjuntamente para crear el sexto parámetro:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

El control se mostrará en el cuadro de diálogo Insertar objeto para contenedores habilitados y será compatible con el modelo de apartamento. Los controles compatibles con el modelo de Apartamento deben garantizar que los datos de la clase estática estén protegidos mediante bloqueos, de modo que, mientras un control de un apartamento esté accediendo a los datos estáticos, no lo deshabilite el programador antes de que finalice y otra instancia de la misma clase empiece a usar los mismos datos estáticos. Cualquier acceso a los datos estáticos se incluirá en el código de sección crítica.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

Registra la clase de página de propiedades con la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de instancia del módulo asociado a la clase de página de propiedades.

*CLSID*<br/>
IDENTIFICADOR de clase único de la página de propiedades.

*idTypeName*<br/>
IDENTIFICADOR de recurso de la cadena que contiene un nombre legible por el usuario para la página de propiedades.

*nRegFlags*<br/>
Puede contener la marca:

- `afxRegApartmentThreading` establece el modelo de subprocesos del registro en ThreadingModel = Apartment.

> [!NOTE]
>  En las versiones de MFC anteriores a MFC 4,2, el parámetro **int** *nRegFlags* no estaba disponible. Tenga en cuenta también que la marca `afxRegInsertable` no es una opción válida para las páginas de propiedades y producirá una ASERCIÓN en MFC si está establecida.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la clase de control se registró; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esto permite que los contenedores que reconocen el control OLE usen la página de propiedades. `AfxOleRegisterPropertyPageClass` actualiza el registro con el nombre de la página de propiedades y su ubicación en el sistema y también establece el modelo de subprocesos que el control admite en el registro. Para obtener más información, vea la [Nota técnica 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "subprocesamiento de modelo Apartamento en controles OLE" y [acerca de los procesos y subprocesos](/windows/win32/ProcThread/about-processes-and-threads) en el Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Registra la biblioteca de tipos en la base de datos de registro de Windows y permite que otros contenedores que reconocen el control OLE utilicen la biblioteca de tipos.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de instancia de la aplicación asociada a la biblioteca de tipos.

*tlid*<br/>
IDENTIFICADOR único de la biblioteca de tipos.

*pszFileName*<br/>
Apunta al nombre de archivo opcional de una biblioteca de tipos localizada (. TLB) del control.

*pszHelpDir*<br/>
Nombre del directorio donde se puede encontrar el archivo de ayuda de la biblioteca de tipos. Si es NULL, se supone que el archivo de ayuda está en el mismo directorio que la propia biblioteca de tipos.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la biblioteca de tipos se registró; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función actualiza el registro con el nombre de la biblioteca de tipos y su ubicación en el sistema.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp. h

##  <a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

Quita la entrada de clase de control o de página de propiedades de la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parámetros

*clsID*<br/>
IDENTIFICADOR único de la clase del control o de la página de propiedades.

*pszProgID*<br/>
IDENTIFICADOR de programa único de la página de control o de propiedades.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se anula correctamente el registro de la clase de página de propiedades o el control. de lo contrario, es 0.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl. h

##  <a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Llame a esta función para quitar la entrada de la biblioteca de tipos de la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parámetros

*tlID*<br/>
IDENTIFICADOR único de la biblioteca de tipos.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha anulado correctamente el registro de la biblioteca de tipos; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
