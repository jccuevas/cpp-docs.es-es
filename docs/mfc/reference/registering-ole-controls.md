---
title: Registrar controles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372972"
---
# <a name="registering-ole-controls"></a>Registrar controles OLE

Otras aplicaciones compatibles con OLE pueden tener acceso a los controles OLE, al igual que otros objetos de servidor OLE. Esto se logra mediante el registro de la biblioteca de tipos y la clase del control.

Las siguientes funciones le permiten agregar y quitar la clase del control, las páginas de propiedades y la biblioteca de tipos en la base de datos de registro de Windows:

### <a name="registering-ole-controls"></a>Registrar controles OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Agrega la clase del control a la base de datos de registro.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Agrega una página de propiedades de control a la base de datos de registro.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Agrega la biblioteca de tipos del control a la base de datos de registro.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Quita una clase de control o una clase de página de propiedades de la base de datos de registro.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Quita la biblioteca de tipos del control de la base de datos de registro.|

`AfxOleRegisterTypeLib`normalmente se llama en la implementación de un archivo DLL de control de `DllRegisterServer`. Del `AfxOleUnregisterTypeLib` mismo modo, es llamado por `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, `AfxOleUnregisterClass` y normalmente `UpdateRegistry` se llama mediante la función miembro de la fábrica de clases o página de propiedades de un control.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

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

*clsid*<br/>
El identificador de clase único del control.

*pszProgID*<br/>
El ID de programa único del control.

*idTypeName*<br/>
El identificador de recurso de la cadena que contiene un nombre de tipo legible por el usuario para el control.

*idBitmap*<br/>
El identificador de recurso del mapa de bits utilizado para representar el control OLE en una barra de herramientas o paleta.

*nRegFlags*<br/>
Contiene uno o varios de los siguientes indicadores:

- `afxRegInsertable`Permite que el control aparezca en el cuadro de diálogo Insertar objeto para objetos OLE.

- `afxRegApartmentThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Apartment.

- `afxRegFreeThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel-Free.

   Puede combinar los `afxRegApartmentThreading` dos `afxRegFreeThreading` indicadores y establecer ThreadingModel-Both. Consulte [InprocServer32](/windows/win32/com/inprocserver32) en el Windows SDK para obtener más información sobre el registro del modelo de subprocesos.

> [!NOTE]
> En las versiones MFC anteriores a MFC 4.2, el parámetro **int** *nRegFlags* era un parámetro BOOL, *bInsertable*, que permitía o no permitía que el control se insertara desde el cuadro de diálogo Insertar objeto.

*dwMiscStatus*<br/>
Contiene uno o varios de los siguientes indicadores de estado (para obtener una descripción de los indicadores, vea enumeración OLEMISC en el Windows SDK):

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
El identificador único de la clase de control.

*wVerMajor*<br/>
El número de versión principal de la clase de control.

*wVerMinor*<br/>
El número de versión secundaria de la clase de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se registró la clase de control; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esto permite que el control sea utilizado por contenedores que son compatibles con el control OLE. `AfxOleRegisterControlClass`actualiza el registro con el nombre y la ubicación del control en el sistema y también establece el modelo de subprocesos que admite el control en el registro. Para obtener más información, vea [Nota técnica 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Subprocesamiento de modelo de apartamento en controles OLE" y Acerca de los [procesos y subprocesos](/windows/win32/ProcThread/about-processes-and-threads) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

En el ejemplo `AfxOleRegisterControlClass` anterior se muestra cómo se llama con el indicador para insertable y el indicador para el modelo de apartamento ORed juntos para crear el sexto parámetro:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

El control se mostrará en el cuadro de diálogo Insertar objeto para contenedores habilitados y será compatible con el modelo de apartamento. Los controles compatibles con el modelo de apartamento deben asegurarse de que los datos de clase estática están protegidos por bloqueos, de modo que mientras un control de un apartamento tiene acceso a los datos estáticos, el programador no lo deshabilita antes de que finalice y otra instancia de la misma clase comience a usar los mismos datos estáticos. Cualquier acceso a los datos estáticos estará rodeado de código de sección crítico.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

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

*clsid*<br/>
El identificador de clase único de la página de propiedades.

*idTypeName*<br/>
El identificador de recurso de la cadena que contiene un nombre legible por el usuario para la página de propiedades.

*nRegFlags*<br/>
Puede contener la bandera:

- `afxRegApartmentThreading`Establece el modelo de subprocesamiento en el registro en ThreadingModel .

> [!NOTE]
> En las versiones de MFC anteriores a MFC 4.2, el parámetro **int** *nRegFlags* no estaba disponible. Tenga en `afxRegInsertable` cuenta también que el indicador no es una opción válida para las páginas de propiedades y provocará un ASSERT en MFC si se establece

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se registró la clase de control; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esto permite que la página de propiedades sea utilizada por contenedores que son compatibles con el control OLE. `AfxOleRegisterPropertyPageClass`actualiza el registro con el nombre de página de propiedades y su ubicación en el sistema y también establece el modelo de subprocesos que admite el control en el registro. Para obtener más información, vea [Nota técnica 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Subprocesamiento de modelo de apartamento en controles OLE" y Acerca de los [procesos y subprocesos](/windows/win32/ProcThread/about-processes-and-threads) en el Windows SDK.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Registra la biblioteca de tipos con la base de datos de registro de Windows y permite que otros contenedores que son compatibles con el control OLE usen la biblioteca de tipos.

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
El identificador único de la biblioteca de tipos.

*pszFileName*<br/>
Apunta al nombre de archivo opcional de una biblioteca de tipos localizada (. TLB) para el control.

*pszHelpDir*<br/>
El nombre del directorio donde se puede encontrar el archivo de ayuda para la biblioteca de tipos. Si NULL, se supone que el archivo de ayuda está en el mismo directorio que la propia biblioteca de tipos.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se registró la biblioteca de tipos; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función actualiza el registro con el nombre de la biblioteca de tipos y su ubicación en el sistema.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

Quita la entrada de clase de control o de propiedad de la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parámetros

*Clsid*<br/>
El identificador de clase único de la página de control o propiedad.

*pszProgID*<br/>
El identificador de programa único de la página de control o propiedad.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control o la clase de página de propiedades se ha anulado correctamente; de lo contrario 0.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Llame a esta función para quitar la entrada de biblioteca de tipos de la base de datos de registro de Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parámetros

*tlID*<br/>
El identificador único de la biblioteca de tipos.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la biblioteca de tipos se ha anulado correctamente; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
