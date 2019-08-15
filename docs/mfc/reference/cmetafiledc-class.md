---
title: Clase Cmetafiledc (
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505504"
---
# <a name="cmetafiledc-class"></a>Clase Cmetafiledc (

Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que puede volver a consultar para crear la imagen o el texto que desee.

## <a name="syntax"></a>Sintaxis

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construye un objeto `CMetaFileDC`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Cierra el contexto del dispositivo y crea un identificador de metarchivo.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Cierra un contexto de dispositivo mejorado y crea un controlador de metarchivo mejorado.|
|[CMetaFileDC::Create](#create)|Crea el contexto de dispositivo de metarchivo de Windows y lo adjunta `CMetaFileDC` al objeto.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crea un contexto de dispositivo de metarchivo para un metarchivo con formato mejorado.|

## <a name="remarks"></a>Comentarios

Para implementar un metarchivo de Windows, primero cree `CMetaFileDC` un objeto. Invoque `CMetaFileDC` el constructor y, a continuación, llame a la función miembro [Create](#create) , que crea un contexto de dispositivo de metarchivo `CMetaFileDC` de Windows y lo adjunta al objeto.

A continuación, `CMetaFileDC` envíe el objeto la secuencia de comandos GDI de CDC que desea que se reproduzcan. Solo se pueden usar los comandos GDI que crean resultados `MoveTo` , `LineTo`como y.

Después de enviar los comandos deseados al metarchivo, llame a la `Close` función miembro, que cierra los contextos de dispositivo de metarchivo y devuelve un identificador de metarchivo. A continuación, elimine el `CMetaFileDC` objeto.

[CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) puede usar el identificador de metarchivo para reproducir el metarchivo varias veces. El metarchivo también puede ser manipulado por funciones de Windows como [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), que copia un metarchivo en el disco.

Cuando el metarchivo ya no sea necesario, elimínelo de la memoria con la función de Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) .

También puede implementar el objeto `CMetaFileDC` para que pueda controlar las llamadas de salida y las llamadas GDI de atributo `GetTextExtent`como. Este tipo de metarchivo es más flexible y puede reutilizar más fácilmente el código GDI general, que a menudo consiste en una combinación de resultados y llamadas de atributo. La `CMetaFileDC` clase hereda dos contextos de dispositivo, `m_hDC` y `m_hAttribDC`, de CDC. El `m_hDC` contexto de dispositivo controla todas las llamadas de salida de `m_hAttribDC` GDI [CDC](../../mfc/reference/cdc-class.md) y el contexto de dispositivo controla todas las llamadas de atributo GDI CDC. Normalmente, estos dos contextos de dispositivo hacen referencia al mismo dispositivo. En el caso de `CMetaFileDC`, el atributo DC está establecido en NULL de forma predeterminada.

Cree un segundo contexto de dispositivo que apunte a la pantalla, una impresora o un dispositivo que no sea un metarchivo y, `SetAttribDC` a continuación, llame a la función miembro para `m_hAttribDC`asociar el nuevo contexto de dispositivo a. Las llamadas de GDI para obtener información ahora se dirigirán `m_hAttribDC`a la nueva. Las llamadas GDI de salida Irán `m_hDC`a, que representa el metarchivo.

Para obtener más información `CMetaFileDC`sobre, vea contextos de [dispositivos](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="close"></a>  CMetaFileDC::Close

Cierra el contexto de dispositivo de metarchivo y crea un identificador de metarchivo de Windows que se puede usar para reproducir el metarchivo mediante la función miembro [CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) .

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valor devuelto

Un HMETAFILE válido si la función se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

El identificador de metarchivo de Windows también se puede utilizar para manipular el metarchivo con funciones de Windows como [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Elimine el metarchivo después de utilizarlo llamando a la función [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) de Windows.

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

Cierra un contexto de dispositivo mejorado y devuelve un identificador que identifica un metarchivo con formato mejorado.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un metarchivo mejorado, si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Una aplicación puede utilizar el identificador de metarchivo mejorado devuelto por esta función para realizar las tareas siguientes:

- Mostrar una imagen almacenada en un metarchivo mejorado

- Crear copias del metarchivo mejorado

- Enumerar, editar o copiar registros individuales en el metarchivo mejorado

- Recuperar una descripción opcional del contenido del metarchivo del encabezado Enhanced-Metafile

- Recuperación de una copia del encabezado Enhanced-Metafile

- Recuperar una copia binaria del metarchivo mejorado

- Enumerar los colores de la paleta opcional

- Convertir un metarchivo con formato mejorado en un metarchivo con formato de Windows

Cuando la aplicación ya no necesita el controlador de metarchivo mejorado, debe liberar el identificador mediante una llamada a `DeleteEnhMetaFile` la función de Win32.

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

Construya un `CMetaFileDC` objeto en dos pasos.

```
CMetaFileDC();
```

### <a name="remarks"></a>Comentarios

En primer lugar `CMetaFileDC`, llame a `Create`y, a continuación, llame a, que crea el contexto de dispositivo `CMetaFileDC` de metarchivo de Windows y lo adjunta al objeto.

##  <a name="create"></a>  CMetaFileDC::Create

Construya un `CMetaFileDC` objeto en dos pasos.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFilename*<br/>
Apunta a una cadena de caracteres terminada en NULL. Especifica el nombre de archivo del metarchivo que se va a crear. Si *lpszFilename* es null, se crea un nuevo metarchivo en memoria.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

En primer lugar, llame `CMetaFileDC`al constructor y `Create`, a continuación, llame a, que crea el contexto de dispositivo de `CMetaFileDC` metarchivo de Windows y lo adjunta al objeto.

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

Crea un contexto de dispositivo para un metarchivo con formato mejorado.

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
Apunta a una cadena de caracteres terminada en NULL. Especifica el nombre de archivo del metarchivo mejorado que se va a crear. Si este parámetro es null, el metarchivo mejorado está basado en memoria y su contenido se pierde cuando se destruye el objeto o cuando `DeleteEnhMetaFile` se llama a la función de Win32.

*lpBounds*<br/>
Apunta a una estructura de datos [Rect](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica las dimensiones de las unidades HIMETRIC (en incrementos de .01-milímetro) de la imagen que se va a almacenar en el metarchivo mejorado.

*lpszDescription*<br/>
Apunta a una cadena terminada en cero que especifica el nombre de la aplicación que creó la imagen, así como el título de la imagen.

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo para el metarchivo mejorado, si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este controlador de dominio se puede usar para almacenar una imagen independiente del dispositivo.

Windows usa el dispositivo de referencia que se identifica mediante el parámetro *pDCRef* para registrar la resolución y las unidades del dispositivo en el que aparecía originalmente una imagen. Si el parámetro *pDCRef* es null, usa el dispositivo de pantalla actual como referencia.

Los miembros izquierdo y superior de la `RECT` estructura de datos a la que apunta el parámetro *lpBounds* deben ser menores que los miembros derecho e inferior, respectivamente. Los puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Si *lpBounds* es null, la interfaz de dispositivo gráfico (GDI) calcula las dimensiones del rectángulo más pequeño que puede incluir la imagen dibujada por la aplicación. Se debe proporcionar el parámetro *lpBounds* siempre que sea posible.

La cadena a la que apunta el parámetro *lpszDescription* debe contener un carácter nulo entre el nombre de la aplicación y el nombre de la imagen y debe terminar con dos caracteres nulos, por ejemplo, "XYZ Graphics Editor\0Bald Eagle\0\0", donde \ 0 representa carácter nulo. Si *lpszDescription* es null, no hay ninguna entrada correspondiente en el encabezado Enhanced-Metafile.

Las aplicaciones usan el DC creado por esta función para almacenar una imagen de gráficos en un metarchivo mejorado. El identificador que identifica este controlador de dominio se puede pasar a cualquier función de GDI.

Una vez que una aplicación almacena una imagen en un metarchivo mejorado, puede mostrar la imagen en cualquier dispositivo de salida llamando `CDC::PlayMetaFile` a la función. Al mostrar la imagen, Windows usa el rectángulo señalado por el parámetro *lpBounds* y los datos de resolución del dispositivo de referencia para colocar y escalar la imagen. El contexto de dispositivo devuelto por esta función contiene los mismos atributos predeterminados asociados a cualquier DC nuevo.

Las aplicaciones deben utilizar la `GetWinMetaFileBits` función de Win32 para convertir un metarchivo mejorado en el formato de metarchivo de Windows anterior.

El nombre de archivo del metarchivo mejorado debe usar. Extensión EMF.

## <a name="see-also"></a>Vea también

[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
