---
title: CMFCAcceleratorKey (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 7d66e7043325bbbd324f3ac443368787a653ebe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369925"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey (clase)

Una clase auxiliar que implementa la asignación y el formato de claves virtuales.

## <a name="syntax"></a>Sintaxis

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construye un objeto `CMFCAcceleratorKey`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKey::Formato](#format)|Traduce la estructura ACCEL a su representación visual.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Establece la tecla `CMFCAcceleratorKey` de método abreviado para el objeto.|

## <a name="remarks"></a>Observaciones

Las teclas del acelerador también se conocen como teclas de método abreviado. Si desea mostrar los métodos abreviados de teclado que un usuario introduce, la [clase CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) asigna métodos abreviados de teclado, como Alt+Mayús+S, a un formato de texto personalizado, como "Alt + Mayús + S". Cada `CMFCAcceleratorKey` objeto asigna una sola tecla de método abreviado a un formato de texto.

Para obtener más información sobre cómo utilizar teclas de método abreviado y tablas de aceleradores, vea [CKeyboardManager (Clase).](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCAcceleratorKey` muestra cómo construir `Format` un objeto y cómo utilizar su método.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxacceleratorkey.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey

Construye un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parámetros

*lpAccel*<br/>
[en] Un puntero a una tecla de método abreviado.

### <a name="remarks"></a>Observaciones

Si no proporciona una tecla de `CMFCAccleratorKey`método abreviado al crear un , utilice el [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) método para asociar una tecla de método abreviado con el `CMFCAcceleratorKey` objeto.

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Formato

Traduce la estructura ACCEL a su valor de cadena asociado.

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
[fuera] Una referencia `CString` a un objeto donde el método escribe la tecla de método abreviado traducida.

### <a name="remarks"></a>Observaciones

Este método recupera el formato de cadena de la tecla de método abreviado asociada. Puede establecer el formato de cadena de un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto utilizando el constructor o el método [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Establece la tecla de método abreviado para el [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objeto.

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parámetros

*lpAccel*<br/>
[en] Un puntero a una tecla de método abreviado.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer `CMFCAcceleratorKey` la tecla de método abreviado para `CMFCAcceleratorKey`un si no proporcionó una tecla de método abreviado al crear el archivo .

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
