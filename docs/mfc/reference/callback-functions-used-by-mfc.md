---
title: "Funciones de devolución de llamada usadas por MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions, MFC
- MFC, callback functions
- functions [C++], callback
- callback functions
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: 08c6f547c95adb4c6794ec71259888d390e42e92
ms.lasthandoff: 03/06/2017

---
# <a name="callback-functions-used-by-mfc"></a>Funciones de devolución de llamada usadas por MFC
Tres funciones de devolución de llamada aparecen en la biblioteca Microsoft Foundation Class. Estas funciones de devolución de llamada se pasan a [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring), y [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc). Tenga en cuenta que todas las funciones de devolución de llamada deben capturar excepciones de MFC antes de volver a Windows, puesto que no se producirán excepciones en los límites de la devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  

|Name||  
|----------|-----------------|  
|[Función de devolución de llamada para CDC::EnumObjects](#enum_objects)||  
|[Función de devolución de llamada para CDC::GrayString](#graystring)||
|[Función de devolución de llamada para CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h 

## <a name="enum_objects"></a>Función de devolución de llamada para CDC:: EnumObjects
El *ObjectFunc* nombre es un marcador de posición para el nombre de la función proporcionada por la aplicación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszLogObject*  
 Apunta a un [LOGPEN](../../mfc/reference/logpen-structure.md) o [LOGBRUSH](../../mfc/reference/logbrush-structure.md) estructura de datos que contiene información acerca de los atributos de la lógicos del objeto.  
  
 `lpData`  
 Apunta a los datos proporcionados por la aplicación pasa a la `EnumObjects` (función).  
  
### <a name="return-value"></a>Valor devuelto  
 La función de devolución de llamada devuelve un `int`. El valor de esta devolución es definido por el usuario. Si la función de devolución de llamada devuelve 0, `EnumObjects` deja de enumeración al principio.  
  
### <a name="remarks"></a>Comentarios  
 Se debe exportar el nombre real.  
  
## <a name="graystring"></a>Función de devolución de llamada para CDC:: graystring
*OutputFunc* es un marcador de posición para el nombre de la función de devolución de llamada proporcionada por la aplicación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Identifica un contexto de dispositivo de memoria con un mapa de bits de al menos el ancho y alto especificado por `nWidth` y `nHeight` a `GrayString`.  
  
 `lpData`  
 Apunta a la cadena de caracteres que se va a dibujar.  
  
 `nCount`  
 Especifica el número de caracteres a la salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor devuelto de la función de devolución de llamada debe ser **TRUE** para indicar éxito; de lo contrario es **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La función de devolución de llamada (*OutputFunc*) debe dibujar una imagen en relación con las coordenadas (0,0) en lugar de (*x*, *y*).  

## <a name="setabortproc"></a>Función de devolución de llamada para CDC:: SETABORTPROC
El nombre *AbortFunc* es un marcador de posición para el nombre de la función proporcionada por la aplicación.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>Parámetros  
 *hPr*  
 Identifica el contexto de dispositivo.  
  
 `code`  
 Especifica si se ha producido un error. Es 0 si no se ha producido ningún error. Es **SP_OUTOFDISK** si el Administrador de impresión está quedando sin espacio y más espacio en disco estará disponible si la aplicación espera. Si `code` es **SP_OUTOFDISK**, la aplicación no tiene que anular el trabajo de impresión. Si no es así, debe dar al administrador de impresión mediante una llamada a la **PeekMessage** o **GetMessage** función de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto de la función de controlador de interrupción es distinto de cero si el trabajo de impresión es continuar y 0 si se cancela.  
  
### <a name="remarks"></a>Comentarios  
 El nombre real debe exportarse como se describe en la sección Comentarios de [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](structures-styles-callbacks-and-message-maps.md)
 [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)
 [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc)
 [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring)


