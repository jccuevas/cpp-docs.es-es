---
title: Clase CMetaFileDC
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
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369950"
---
# <a name="cmetafiledc-class"></a>Clase CMetaFileDC

Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que puede volver a consultar para crear la imagen o el texto que desee.

## <a name="syntax"></a>Sintaxis

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construye un objeto `CMetaFileDC`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMetaFileDC::Cerrar](#close)|Cierra el contexto del dispositivo y crea un identificador de metarchivo.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Cierra un contexto de dispositivo de metarchivo mejorado y crea un identificador de metarchivo mejorado.|
|[CMetaFileDC::Crear](#create)|Crea el contexto del dispositivo de metarchivo de Windows y lo adjunta al `CMetaFileDC` objeto.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crea un contexto de dispositivo de metarchivo para un metarchivo de formato mejorado.|

## <a name="remarks"></a>Observaciones

Para implementar un metarchivo de `CMetaFileDC` Windows, primero cree un objeto. Invoque el `CMetaFileDC` constructor y, a continuación, llame a la [create](#create) función miembro, que crea un contexto de dispositivo de metarchivo de Windows y lo adjunta al `CMetaFileDC` objeto.

A continuación, envíe al `CMetaFileDC` objeto la secuencia de comandos GDI de CDC que desea que se reproduzca. Solo se pueden utilizar los comandos GDI que crean la salida, como `MoveTo` y `LineTo`, .

Después de haber enviado los comandos `Close` deseados al metarchivo, llame a la función miembro, que cierra los contextos del dispositivo de metarchivo y devuelve un identificador de metarchivo. A continuación, `CMetaFileDC` deseche el objeto.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) puede usar el identificador de metarchivo para reproducir el metarchivo repetidamente. El metarchivo también puede ser manipulado por funciones de Windows como [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), que copia un metarchivo en el disco.

Cuando el metarchivo ya no sea necesario, elimínelo de la memoria con la función [DeTMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) de Windows.

También puede implementar `CMetaFileDC` el objeto para que pueda controlar tanto las `GetTextExtent`llamadas de salida como las llamadas GDI de atributo como . Este tipo de metarchivo es más flexible y puede reutilizar más fácilmente el código GDI general, que a menudo consiste en una combinación de llamadas de salida y atributo. La `CMetaFileDC` clase hereda dos `m_hDC` contextos de dispositivo y `m_hAttribDC`, de CDC. El `m_hDC` contexto del dispositivo controla todas `m_hAttribDC` las llamadas de salida GDI de [CDC](../../mfc/reference/cdc-class.md) y el contexto del dispositivo controla todas las llamadas de atributo GDI de CDC. Normalmente, estos dos contextos del dispositivo refieren al mismo dispositivo. En el `CMetaFileDC`caso de , el atributo DC se establece en NULL de forma predeterminada.

Cree un segundo contexto de dispositivo que apunte a la pantalla, una `SetAttribDC` impresora o un dispositivo `m_hAttribDC`que no sea un metarchivo y, a continuación, llame a la función miembro para asociar el nuevo contexto de dispositivo con . Las llamadas de información de GDI ahora se dirigirán a la nueva `m_hAttribDC`. Las llamadas GDI `m_hDC`de salida irán a , que representa el metarchivo.

Para obtener `CMetaFileDC`más información sobre , consulte [Contextos](../../mfc/device-contexts.md)de dispositivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Cerrar

Cierra el contexto del dispositivo de metarchivo y crea un identificador de metarchivo de Windows que se puede usar para reproducir el metarchivo mediante el [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) función miembro.

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valor devuelto

Un HMETAFILE válido si la función se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

El identificador de metarchivo de Windows también se puede utilizar para manipular el metarchivo con funciones de Windows como [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Elimine el metarchivo después de usarlo llamando a la función [DeleteMetaFile de](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows.

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced

Cierra un contexto de dispositivo de metarchivo mejorado y devuelve un identificador que identifica un metarchivo de formato mejorado.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valor devuelto

Un identificador de un metarchivo mejorado, si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Una aplicación puede utilizar el identificador de metarchivo mejorado devuelto por esta función para realizar las siguientes tareas:

- Mostrar una imagen almacenada en un metarchivo mejorado

- Crear copias del metarchivo mejorado

- Enumerar, editar o copiar registros individuales en el metarchivo mejorado

- Recuperar una descripción opcional del contenido del metarchivo del encabezado del metarchivo mejorado

- Recuperar una copia del encabezado de metarchivo mejorado

- Recuperar una copia binaria del metarchivo mejorado

- Enumerar los colores en la paleta opcional

- Convertir un metarchivo de formato mejorado en un metarchivo de formato Windows

Cuando la aplicación ya no necesita el identificador de metarchivo mejorado, debe liberar el identificador mediante una llamada a la función Win32. `DeleteEnhMetaFile`

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC

Construir `CMetaFileDC` un objeto en dos pasos.

```
CMetaFileDC();
```

### <a name="remarks"></a>Observaciones

En primer `CMetaFileDC`lugar, `Create`llame a , a continuación, llame a `CMetaFileDC` , que crea el contexto del dispositivo de metarchivo de Windows y lo adjunta al objeto.

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Crear

Construir `CMetaFileDC` un objeto en dos pasos.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFilename*<br/>
Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo del metarchivo que se va a crear. Si *lpszFilename* es NULL, se crea un nuevo metarchivo en memoria.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

En primer lugar, llame al constructor `CMetaFileDC`y, a continuación, llame a `Create`, que crea el contexto del dispositivo de metarchivo de Windows y lo adjunta al `CMetaFileDC` objeto.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced

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
Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo del metarchivo mejorado que se va a crear. Si este parámetro es NULL, el metarchivo mejorado se basa en la memoria y `DeleteEnhMetaFile` su contenido se pierde cuando se destruye el objeto o cuando se llama a la función Win32.

*lpBounds*<br/>
Apunta a una estructura de datos [RECT](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica las dimensiones de las unidades HIMETRIC (en incrementos de .01 milímetros) de la imagen que se va a almacenar en el metarchivo mejorado.

*lpszDescription*<br/>
Apunta a una cadena terminada en cero que especifica el nombre de la aplicación que creó la imagen, así como el título de la imagen.

### <a name="return-value"></a>Valor devuelto

Un identificador del contexto del dispositivo para el metarchivo mejorado, si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Este controlador de dominio se puede utilizar para almacenar una imagen independiente del dispositivo.

Windows utiliza el dispositivo de referencia identificado por el parámetro *pDCRef* para registrar la resolución y las unidades del dispositivo en el que apareció originalmente una imagen. Si el *pDCRef* parámetro es NULL, utiliza el dispositivo de visualización actual como referencia.

Los miembros izquierdo `RECT` y superior de la estructura de datos a la que apunta el parámetro *lpBounds* deben ser más pequeños que los miembros derecho e inferior, respectivamente. Los puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Si *lpBounds* es NULL, la interfaz de dispositivo gráfico (GDI) calcula las dimensiones del rectángulo más pequeño que puede incluir la imagen dibujada por la aplicación. El parámetro *lpBounds* debe proporcionarse siempre que sea posible.

La cadena señalada por el parámetro *lpszDescription* debe contener un carácter nulo entre el nombre de la aplicación y el nombre de la imagen y debe terminar con dos caracteres nulos, por ejemplo, "XYZ Graphics Editor-0Bald Eagle-0-0", donde el valor de "0 representa el carácter nulo". Si *lpszDescription* es NULL, no hay ninguna entrada correspondiente en el encabezado enhanced-metafile.

Las aplicaciones utilizan el controlador de dominio creado por esta función para almacenar una imagen gráfica en un metarchivo mejorado. El identificador que identifica este controlador de dominio se puede pasar a cualquier función GDI.

Después de que una aplicación almacena una imagen en un metarchivo `CDC::PlayMetaFile` mejorado, puede mostrar la imagen en cualquier dispositivo de salida llamando a la función. Al mostrar la imagen, Windows utiliza el rectángulo al que apunta el parámetro *lpBounds* y los datos de resolución del dispositivo de referencia para colocar y escalar la imagen. El contexto de dispositivo devuelto por esta función contiene los mismos atributos predeterminados asociados a cualquier nuevo controlador de dominio.

Las aplicaciones deben utilizar `GetWinMetaFileBits` la función Win32 para convertir un metarchivo mejorado al formato de metarchivo de Windows anterior.

El nombre de archivo del metarchivo mejorado debe utilizar el archivo . Extensión EMF.

## <a name="see-also"></a>Consulte también

[Clase CDC](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
