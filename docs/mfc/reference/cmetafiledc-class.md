---
title: CMetaFileDC (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4b19358b97ca0afbe7a70347e5b05bed9916846
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076352"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC (clase)

Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que puede volver a consultar para crear la imagen o el texto que desee.

## <a name="syntax"></a>Sintaxis

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construye un objeto `CMetaFileDC`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Cierra el contexto de dispositivo y crea un identificador del metarchivo.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Cierra un contexto de dispositivo de metarchivo mejorado y crea un identificador del metarchivo mejorado.|
|[CMetaFileDC::Create](#create)|Crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crea un contexto de dispositivo de metarchivo de un metarchivo mejorado de formato.|

## <a name="remarks"></a>Comentarios

Para implementar un metarchivo de Windows, cree primero un `CMetaFileDC` objeto. Invocar el `CMetaFileDC` constructor, a continuación, llame a la [crear](#create) función miembro, que crea un contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.

Después de enviar el `CMetaFileDC` la secuencia de comandos para que pueda reproducir CDC GDI que piensa de objeto. Solo esos comandos GDI que crean como resultado, `MoveTo` y `LineTo`, se puede usar.

Después de enviar los comandos que quiera en el metarchivo, llame a la `Close` función miembro, lo que cierra los contextos de dispositivo de metarchivo y devuelve un identificador del metarchivo. A continuación, eliminarlos de la `CMetaFileDC` objeto.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) , a continuación, se puede usar el identificador del metarchivo para reproducir varias veces el metarchivo. Metarchivo también se puede manipular con las funciones de Windows como [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea), que copia un metarchivo en el disco.

Cuando ya no se necesita el metarchivo, eliminarlo de la memoria con el [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) función de Windows.

También puede implementar la `CMetaFileDC` de objeto que puede controlar tanto las llamadas de salida y atributo, como llamadas GDI `GetTextExtent`. Este tipo de un metarchivo es más flexible y pueden más fácilmente reutilizar código general de GDI, lo que a menudo se compone de una combinación de las llamadas de salida y el atributo. El `CMetaFileDC` clase hereda de dos contextos de dispositivo, `m_hDC` y `m_hAttribDC`, de CDC. El `m_hDC` contexto de dispositivo encarga de toda [CDC](../../mfc/reference/cdc-class.md) GDI llamadas de salida y el `m_hAttribDC` contexto de dispositivo controla todas las llamadas de atributo CDC GDI. Normalmente, estos contextos de dos dispositivo hacen referencia al mismo dispositivo. En el caso de `CMetaFileDC`, el controlador de dominio de atributo se establece en NULL de forma predeterminada.

Crear un segundo contexto de dispositivo que apunta a la pantalla, una impresora o dispositivo que no sea un metarchivo, a continuación, llame a la `SetAttribDC` función miembro para asociar el nuevo contexto de dispositivo con `m_hAttribDC`. Las llamadas GDI para obtener información se dirigirán a la nueva `m_hAttribDC`. Llamadas de salida GDI irá a `m_hDC`, que representa el metarchivo.

Para obtener más información sobre `CMetaFileDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

Cierra el contexto de dispositivo de metarchivo y crea un identificador del metarchivo de Windows que se puede usar para reproducir el metarchivo mediante el [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) función miembro.

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valor devuelto

Un HMETAFILE válido si la función se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

El identificador del metarchivo de Windows también puede usarse para manipular el metarchivo con funciones de Windows como [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea).

Elimina el metarchivo tras su uso mediante una llamada a la Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) función.

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

Cierra un contexto de dispositivo de metarchivo mejorado y devuelve un identificador que identifica un metarchivo mejorado de formato.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valor devuelto

Un identificador de un metarchivo mejorado, si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Una aplicación puede usar el identificador del metarchivo mejorado devuelto por esta función para realizar las siguientes tareas:

- Mostrar una imagen almacenada en un metarchivo mejorado

- Crear copias del metarchivo mejorado

- Enumerar, editar o copiar registros individuales del metarchivo mejorado

- Recuperar una descripción opcional del contenido del metarchivo en el encabezado de metarchivo mejorado

- Recuperar una copia del encabezado de metarchivo mejorado

- Recuperar una copia binaria del metarchivo mejorado

- Enumerar los colores de la paleta opcional

- Convertir un metarchivo mejorado de formato en un metarchivo de Windows-format

Cuando la aplicación ya no necesita el identificador del metarchivo mejorado, debe liberar el identificador mediante una llamada a Win32 `DeleteEnhMetaFile` función.

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

Construir un `CMetaFileDC` objeto en dos pasos.

```
CMetaFileDC();
```

### <a name="remarks"></a>Comentarios

En primer lugar, llame a `CMetaFileDC`, a continuación, llame a `Create`, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.

##  <a name="create"></a>  CMetaFileDC::Create

Construir un `CMetaFileDC` objeto en dos pasos.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFilename*<br/>
Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo del metarchivo que se va a crear. Si *lpszFilename* es NULL, se crea un nuevo metarchivo en memoria.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

En primer lugar, llame al constructor `CMetaFileDC`, a continuación, llame a `Create`, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

Crea un contexto de dispositivo para un metarchivo de formato mejorado.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parámetros

*pDCRef*<br/>
Identifica un dispositivo de referencia para el metarchivo mejorado.

*lpszFileName*<br/>
Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo para el metarchivo mejorado para crearse. Si este parámetro es NULL, el metarchivo mejorado está basada en memoria y su contenido que se pierde cuando se destruye el objeto o cuando Win32 `DeleteEnhMetaFile` se llama a la función.

*lpBounds*<br/>
Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura de datos o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las dimensiones en unidades HIMETRIC (en incrementos de.01 milímetro) de la imagen que se almacenará en el metarchivo mejorado.

*lpszDescripción*<br/>
Apunta a una cadena terminada en cero que especifica el nombre de la aplicación que creó la imagen, así como el título de la imagen.

### <a name="return-value"></a>Valor devuelto

Un identificador del contexto de dispositivo de metarchivo mejorado, si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Este controlador de dominio puede utilizarse para almacenar una imagen independiente del dispositivo.

Windows usa el dispositivo de referencia identificado por el *pDCRef* parámetro para registrar la resolución y las unidades del dispositivo en el que apareció originalmente una imagen. Si el *pDCRef* parámetro es NULL, usa el dispositivo de pantalla actual como referencia.

Los miembros izquierdos y superiores de la `RECT` estructura de datos que apunta el *lpBounds* parámetro debe ser inferior a los miembros de la derecha y abajo, respectivamente. Puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Si *lpBounds* es NULL, la interfaz de dispositivo gráfico (GDI) calcula las dimensiones del rectángulo más pequeño que puede incluir la imagen dibujada por la aplicación. El *lpBounds* parámetro debe especificarse siempre que sea posible.

La cadena señalada por el *lpszDescripción* parámetro debe contener un carácter nulo entre el nombre de la aplicación y el nombre de imagen y debe terminar con dos caracteres null, por ejemplo, "XYZ gráficos Editor\0Bald Eagle\0\0, "donde \0 representa el carácter nulo. Si *lpszDescripción* es NULL, no hay ninguna entrada correspondiente en el encabezado de metarchivo mejorado.

Las aplicaciones utilizar el controlador de dominio creado por esta función para almacenar una imagen de gráficos en un metarchivo mejorado. El identificador que identifica este controlador de dominio puede pasarse a cualquier función GDI.

Después de una aplicación almacena una imagen en un metarchivo mejorado, puede mostrar la imagen en cualquier dispositivo de salida mediante una llamada a la `CDC::PlayMetaFile` función. Cuando se muestra la imagen, Windows utiliza el rectángulo que apunta el *lpBounds* parámetro y los datos de la resolución del dispositivo de referencia de posición y escalar la imagen. El contexto de dispositivo devuelto por esta función contiene los mismos atributos predeterminado asociados con cualquier controlador de dominio nuevo.

Las aplicaciones deben usar Win32 `GetWinMetaFileBits` función para convertir un metarchivo mejorado en el formato de metarchivo de Windows anterior.

Debe usar el nombre de archivo para el metarchivo mejorado el. Extensión EMF.

## <a name="see-also"></a>Vea también

[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

