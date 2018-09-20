---
title: CMFCAcceleratorKey (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09654021af146ba48654c361b7b75302ffcfa34c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420775"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey (clase)

Una clase auxiliar que implementa la asignación de clave virtual y el formato.

## <a name="syntax"></a>Sintaxis

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construye un objeto `CMFCAcceleratorKey`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|Convierte la estructura de aceleración en su representación visual.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Establece la tecla de método abreviado para el `CMFCAcceleratorKey` objeto.|

## <a name="remarks"></a>Comentarios

Teclas de aceleración también conocido como son teclas de método abreviado. Si desea mostrar los métodos abreviados de teclado que un usuario escribe, la [clase CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) asignaciones de teclado accesos directos a un formato de texto personalizado, como "Alt + Mayús + S", como Alt + Mayús + S. Cada `CMFCAcceleratorKey` objeto asigna una clave de acceso directo único en un formato de texto.

Para obtener más información sobre cómo usar las teclas de método abreviado y tablas de aceleradores, consulte [CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCAcceleratorKey` objeto y cómo usar su `Format` método.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

Construye un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parámetros

*lpAccel*<br/>
[in] Un puntero a una tecla de método abreviado.

### <a name="remarks"></a>Comentarios

Si no se proporcione una tecla de método abreviado cuando creas un `CMFCAccleratorKey`, utilice el [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) para asociar una tecla de método abreviado con su `CMFCAcceleratorKey` objeto.

##  <a name="format"></a>  CMFCAcceleratorKey::Format

Convierte la estructura de aceleración en su valor de cadena asociado.

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
[out] Una referencia a un `CString` donde el método escribe la tecla de método abreviado traducido del objeto.

### <a name="remarks"></a>Comentarios

Este método recupera el formato de cadena de la tecla de método abreviado. Puede establecer el formato de cadena de un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto utilizando el constructor o el método [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

Establece la tecla de método abreviado para el [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parámetros

*lpAccel*<br/>
[in] Un puntero a una tecla de método abreviado.

### <a name="remarks"></a>Comentarios

Use este método para establecer la tecla de método abreviado para un `CMFCAcceleratorKey` si no proporcionó una tecla de método abreviado cuando creó el `CMFCAcceleratorKey`.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md)
