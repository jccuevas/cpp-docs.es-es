---
title: Funciones de devolución de llamada usadas por MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 9e51774b2158a81fce05dc0bd27e296e4ad94faa
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424762"
---
# <a name="callback-functions-used-by-mfc"></a>Funciones de devolución de llamada usadas por MFC

En el biblioteca MFC aparecen tres funciones de devolución de llamada. Estas funciones de devolución de llamada se pasan a [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)y [CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Tenga en cuenta que todas las funciones de devolución de llamada deben interceptar excepciones de MFC antes de volver a Windows, ya que no se pueden iniciar excepciones en los límites de devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

|Nombre||
|----------|-----------------|
|[Función de devolución de llamada para CDC::EnumObjects](#enum_objects)||
|[Función de devolución de llamada para CDC::GrayString](#graystring)||
|[Función de devolución de llamada para CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="enum_objects"></a>Función de devolución de llamada para CDC:: EnumObjects

El nombre *ObjectFunc* es un marcador de posición para el nombre de la función proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parámetros

*lpszLogObject*<br/>
Apunta a una estructura de datos [logpen (](/windows/win32/api/Wingdi/ns-wingdi-logpen) o [logbrush (](/windows/win32/api/wingdi/ns-wingdi-logbrush) que contiene información sobre los atributos lógicos del objeto.

*lpData*<br/>
Apunta a los datos proporcionados por la aplicación pasados a la función `EnumObjects`.

### <a name="return-value"></a>Valor devuelto

La función de devolución de llamada devuelve un valor **int**. El valor de esta devolución está definido por el usuario. Si la función de devolución de llamada devuelve 0, `EnumObjects` detiene la enumeración pronto.

### <a name="remarks"></a>Observaciones

Se debe exportar el nombre real.

## <a name="graystring"></a>Función de devolución de llamada para CDC:: GrayString

*OutputFunc* es un marcador de posición para el nombre de la función de devolución de llamada proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parámetros

*Cámaras*<br/>
Identifica un contexto de dispositivo de memoria con un mapa de bits de al menos el ancho y el alto especificados por `nWidth` y `nHeight` a `GrayString`.

*lpData*<br/>
Apunta a la cadena de caracteres que se va a dibujar.

*nCount*<br/>
Especifica el número de caracteres que se van a generar.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de la función de devolución de llamada debe ser TRUE para indicar que se ha realizado correctamente; en caso contrario, es FALSE.

### <a name="remarks"></a>Observaciones

La función de devolución de llamada (*OutputFunc*) debe dibujar una imagen en relación con las coordenadas (0,0) en lugar de (*x*, *y*).

## <a name="setabortproc"></a>Función de devolución de llamada para CDC:: SetAbortProc

El nombre *AbortFunc* es un marcador de posición para el nombre de la función proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parámetros

*hPr*<br/>
Identifica el contexto del dispositivo.

*code*<br/>
Especifica si se ha producido un error. Es 0 si no se ha producido ningún error. Se SP_OUTOFDISK si el administrador de impresión tiene actualmente espacio en disco y hay más espacio disponible en disco si la aplicación espera. Si el *código* es SP_OUTOFDISK, la aplicación no tiene que anular el trabajo de impresión. Si no es así, debe proporcionar al administrador de impresión una llamada a la función de Windows `PeekMessage` o `GetMessage`.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de la función Abort-handler es distinto de cero si el trabajo de impresión va a continuar y 0 si se cancela.

### <a name="remarks"></a>Observaciones

El nombre real debe exportarse tal y como se describe en la sección Comentarios de [CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)
