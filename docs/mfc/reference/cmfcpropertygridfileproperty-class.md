---
title: CMFCPropertyGridFileProperty (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 20a0a50198357602d70a2111c6884058f7578af7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326714"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty (clase)

La `CMFCPropertyGridFileProperty` clase es compatible con un elemento de control de lista de propiedades que se abre un cuadro de diálogo de selección de archivos.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Construye un objeto `CMFCPropertyGridFileProperty`.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Invalida [cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

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
[in] El nombre de propiedad.

*bOpenFileDialog*<br/>
[in] True para abrir un **abrir archivo** cuadro de diálogo; FALSE para abrir un **Guardar archivo** cuadro de diálogo.

*strFileName*<br/>
[in] El nombre de archivo inicial.

*lpszDefExt*<br/>
[in] Una cadena de uno o más extensiones de nombre de archivo. El valor predeterminado es NULL.

*dwFlags*<br/>
[in] Marcas de cuadro de diálogo. El valor predeterminado es una combinación bit a bit (OR) de OFN_HIDEREADONLY y OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[in] Una cadena de uno o varios filtros de archivo. El valor predeterminado es NULL.

*lpszDescr*<br/>
[in] La descripción del elemento de propiedad. El valor predeterminado es NULL.

*dwData*<br/>
[in] Datos específicos de la aplicación que está asociados con el elemento de propiedad. Por ejemplo, un entero de 32 bits o un puntero a otros datos. El valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Para obtener una lista completa de los indicadores disponibles, vea [estructura OPENFILENAME](/windows/desktop/api/commdlg/ns-commdlg-tagofna).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto mediante el constructor de la clase `CMFCPropertyGridFileProperty`. Este ejemplo forma parte de la [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
