---
title: CMFCPropertyGridFileProperty (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360580"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty (Clase)

La `CMFCPropertyGridFileProperty` clase admite un elemento de control de lista de propiedades que abre un cuadro de diálogo de selección de archivos.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Construye un objeto `CMFCPropertyGridFileProperty`.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Reemplaza [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Observaciones

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

Construye un objeto `CMFCPropertyGridFileProperty`.

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
[in] Nombre de la propiedad.

*bOpenFileDialog*<br/>
[en] TRUE para abrir un cuadro de diálogo **Abrir archivo;** FALSE para abrir un cuadro de diálogo **Guardar archivo.**

*strFileName*<br/>
[en] El nombre de archivo inicial.

*lpszDefExt*<br/>
[en] Cadena de una o más extensiones de nombre de archivo. El valor predeterminado es NULL.

*dwFlags*<br/>
[en] Marcas de cuadro de diálogo. El valor predeterminado es una combinación bit a bit (OR) de OFN_HIDEREADONLY y OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[en] Una cadena de uno o más filtros de archivo. El valor predeterminado es NULL.

*lpszDescr*<br/>
[en] La descripción del elemento de propiedad. El valor predeterminado es NULL.

*dwData*<br/>
[en] Datos específicos de la aplicación asociados al elemento de propiedad. Por ejemplo, un entero de 32 bits o un puntero a otros datos. El valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Para obtener una lista completa de los indicadores disponibles, consulte [Estructura OPENFILENAME](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto mediante el constructor de la clase `CMFCPropertyGridFileProperty`. Este ejemplo forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (Clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
