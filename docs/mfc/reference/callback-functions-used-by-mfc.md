---
title: Funciones de devolución de llamada usadas por MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371138"
---
# <a name="callback-functions-used-by-mfc"></a>Funciones de devolución de llamada usadas por MFC

Aparecen tres funciones de devolución de llamada en la biblioteca Microsoft Foundation Class. Estas funciones de devolución de llamada se pasan a [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)y [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Tenga en cuenta que todas las funciones de devolución de llamada deben capturar excepciones MFC antes de volver a Windows, ya que las excepciones no se pueden producir a través de los límites de devolución de llamada. Para obtener más información acerca de las excepciones, vea el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).

|Nombre||
|----------|-----------------|
|[Función de devolución de llamada para CDC::EnumObjects](#enum_objects)||
|[Función de devolución de llamada para CDC::GrayString](#graystring)||
|[Función de devolución de llamada para CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Función de devolución de llamada para CDC::EnumObjects

El nombre *ObjectFunc* es un marcador de posición para el nombre de función proporcionado por la aplicación.

### <a name="syntax"></a>Sintaxis

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parámetros

*lpszLogObject*<br/>
Apunta a una estructura de datos [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) o [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) que contiene información sobre los atributos lógicos del objeto.

*lpData*<br/>
Señala los datos proporcionados por `EnumObjects` la aplicación pasados a la función.

### <a name="return-value"></a>Valor devuelto

La función de devolución de llamada devuelve un **int**. El valor de este retorno está definido por el usuario. Si la función `EnumObjects` de devolución de llamada devuelve 0, detiene la enumeración antes de tiempo.

### <a name="remarks"></a>Observaciones

El nombre real debe exportarse.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Función de devolución de llamada para CDC::GrayString

*OutputFunc* es un marcador de posición para el nombre de la función de devolución de llamada proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parámetros

*Hdc*<br/>
Identifica un contexto de dispositivo de memoria con un mapa `nWidth` `nHeight` de `GrayString`bits de al menos el ancho y alto especificados por y para .

*lpData*<br/>
Apunta a la cadena de caracteres que se va a dibujar.

*nCount*<br/>
Especifica el número de caracteres que se va a generar.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de la función de devolución de llamada debe ser TRUE para indicar el éxito; de lo contrario es FALSE.

### <a name="remarks"></a>Observaciones

La función de devolución de llamada (*OutputFunc*) debe dibujar una imagen en relación con las coordenadas (0,0) en lugar de (*x*, *y*).

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Función de devolución de llamada para CDC::SetAbortProc

El nombre *AbortFunc* es un marcador de posición para el nombre de función proporcionado por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parámetros

*Hpr*<br/>
Identifica el contexto del dispositivo.

*Código*<br/>
Especifica si se ha producido un error. Es 0 si no se ha producido ningún error. Es SP_OUTOFDISK si el Administrador de impresión está actualmente sin espacio en disco y más espacio en disco estará disponible si la aplicación espera. Si el *código* está SP_OUTOFDISK, la aplicación no tiene que anular el trabajo de impresión. Si no es así, debe ceder al `PeekMessage` Administrador `GetMessage` de impresión llamando a la función o Windows.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de la función de controlador de anulación es distinto de cero si el trabajo de impresión va a continuar y 0 si se cancela.

### <a name="remarks"></a>Observaciones

El nombre real debe exportarse como se describe en la sección Comentarios de [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
