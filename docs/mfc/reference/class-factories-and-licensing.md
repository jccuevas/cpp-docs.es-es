---
title: Generadores de clases y licencias
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611844"
---
# <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

Para crear una instancia del control OLE, una aplicación de contenedor llama a una función miembro de la fábrica de clase del control. Dado que el control es un objeto OLE real, el generador de clases es responsable de crear instancias del control. Cada clase de control OLE debe tener un generador de clases.

Otra característica importante de los controles OLE es su capacidad para aplicar una licencia. ControlWizard permite incorporar las licencias durante la creación de su proyecto de control. Para obtener más información acerca de las licencias de control, vea el artículo [controles ActiveX: Licencias de un Control ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

La tabla siguiente enumeran varias macros y funciones que se usan para declarar e implementar el generador de clases de su control y a la licencia de su control.

### <a name="class-factories-and-licensing"></a>Generadores de clases y licencias

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Declara el generador de clases para una página de control o la propiedad OLE.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa el control `GetClassID` de función y declara una instancia de la fábrica de clase.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Comienza la declaración de las funciones de administración de licencias.|
|[END_OLEFACTORY](#end_olefactory)|Finaliza la declaración de las funciones de administración de licencias.|
|[AfxVerifyLicFile](#afxverifylicfile)|Comprueba si un control tiene licencia para su uso en un equipo determinado.|

##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX

Declara un generador de clases y el `GetClassID` función miembro de la clase del control.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control.

### <a name="remarks"></a>Comentarios

Use esta macro en el archivo de encabezado de la clase de control para un control que no es compatible con las licencias.

Tenga en cuenta que esta macro tiene la misma finalidad que el ejemplo de código siguiente:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX

Implementa el generador de clases de su control y el [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) función miembro de la clase del control.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de página de propiedades de control.

*external_name*<br/>
El nombre de objeto expuesto a las aplicaciones.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Componentes de CLSID de la clase. Para obtener más información acerca de estos parámetros, vea la sección Comentarios para [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Comentarios

Esta macro debe aparecer en el archivo de implementación de cualquier clase de control que usa el declare_olecreate_ex (macro) o las macros BEGIN_OLEFACTORY y END_OLEFACTORY. External name es el identificador del control OLE que se expone a otras aplicaciones. Contenedores usan este nombre para solicitar un objeto de esta clase de control.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY

Comienza la declaración de su generador de clases en el archivo de encabezado de la clase del control.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Especifica el nombre de la clase control cuyo generador de clases que se trata.

### <a name="remarks"></a>Comentarios

Las declaraciones de licencias de las funciones de generador de clases deben comenzar inmediatamente después de BEGIN_OLEFACTORY.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="end_olefactory"></a>  END_OLEFACTORY

Finaliza la declaración del generador de clases de su control.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase control cuyo generador de clases que se trata.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

##  <a name="afxverifylicfile"></a>  AfxVerifyLicFile

Llame a esta función para comprobar que el archivo de licencia denominado por `pszLicFileName` es válido para el control OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
El identificador de instancia de la DLL asociada al control con licencia.

*pszLicFileName*<br/>
Apunta a una cadena de caracteres terminada en null que contiene el nombre de archivo de licencia.

*pszLicFileContents*<br/>
Señala a una secuencia de bytes que debe coincidir con la secuencia que se encuentra al principio del archivo de licencia.

*cch*<br/>
Número de caracteres de *pszLicFileContents*.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo de licencia existe y comienza con la secuencia de caracteres en *pszLicFileContents*; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Si *cch* es -1, esta función utiliza:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxctl.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
