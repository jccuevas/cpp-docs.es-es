---
title: Funciones de devolución de llamada usadas por MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3093ca60b222512e517400f478fc9d635a6f867
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073778"
---
# <a name="callback-functions-used-by-mfc"></a>Funciones de devolución de llamada usadas por MFC

Tres funciones de devolución de llamada aparecen en la biblioteca Microsoft Foundation Class. Estas funciones de devolución de llamada se pasan a [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring), y [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc). Tenga en cuenta que todas las funciones de devolución de llamada deben interceptar las excepciones de MFC antes de volver a Windows, puesto que no se puede producir excepciones en los límites de devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).

|nombre||
|----------|-----------------|
|[Función de devolución de llamada para CDC::EnumObjects](#enum_objects)||
|[Función de devolución de llamada para CDC::GrayString](#graystring)||
|[Función de devolución de llamada para CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="enum_objects"></a> Función de devolución de llamada para CDC:: EnumObjects

El *ObjectFunc* nombre es un marcador de posición para el nombre de función proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parámetros

*lpszLogObject*<br/>
Apunta a un [LOGPEN](../../mfc/reference/logpen-structure.md) o [LOGBRUSH](../../mfc/reference/logbrush-structure.md) estructura de datos que contiene información sobre los atributos de la lógicas del objeto.

*lpData*<br/>
Apunta a los datos proporcionados por la aplicación pasa a la `EnumObjects` función.

### <a name="return-value"></a>Valor devuelto

La función de devolución de llamada devuelve un **int**. El valor de esta devolución es definido por el usuario. Si la función de devolución de llamada devuelve 0, `EnumObjects` deja de enumeración al principio.

### <a name="remarks"></a>Comentarios

El nombre real se debe exportar.

## <a name="graystring"></a>  Función de devolución de llamada para CDC:: graystring

*OutputFunc* es un marcador de posición para el nombre de la función de devolución de llamada proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parámetros

*hDC*<br/>
Identifica un contexto de dispositivo de memoria con un mapa de bits de al menos el ancho y alto especificados por `nWidth` y `nHeight` a `GrayString`.

*lpData*<br/>
Apunta a la cadena de caracteres que se va a dibujar.

*nCount*<br/>
Especifica el número de caracteres a la salida.

### <a name="return-value"></a>Valor devuelto

Valor devuelto de la función de devolución de llamada debe ser TRUE para indicar que es correcto; en caso contrario, es FALSE.

### <a name="remarks"></a>Comentarios

La función de devolución de llamada (*OutputFunc*) debe dibujar una imagen en relación con las coordenadas (0,0) en lugar de (*x*, *y*).

## <a name="setabortproc"></a>  Función de devolución de llamada para CDC:: SETABORTPROC

El nombre *AbortFunc* es un marcador de posición para el nombre de función proporcionada por la aplicación.

### <a name="syntax"></a>Sintaxis

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parámetros

*hPr*<br/>
Identifica el contexto de dispositivo.

*code*<br/>
Especifica si se ha producido un error. Es 0 si no se ha producido ningún error. Es SP_OUTOFDISK si el Administrador de impresión se está quedando sin espacio y más espacio en disco estará disponible si la aplicación espera. Si *código* es SP_OUTOFDISK, la aplicación no tiene que anular el trabajo de impresión. Si no es así, debe dar al administrador de impresión mediante una llamada a la `PeekMessage` o `GetMessage` función de Windows.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de la función de controlador de la anulación es distinto de cero si el trabajo de impresión es para continuar y 0 si se cancela.

### <a name="remarks"></a>Comentarios

El nombre real debe exportarse como se describe en la sección Comentarios de [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC:: graystring](../../mfc/reference/cdc-class.md#graystring)

