---
title: CMFCDesktopAlertWndInfo Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: a4b3d8769b3d267c0bd3f81269dd3b8ab3cf3184
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403651"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo Class

El `CMFCDesktopAlertWndInfo` clase se utiliza con el [clase CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md). Especifica los controles que se muestran si emerge la ventana de alerta de escritorio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Identificador del icono que se muestra.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|El identificador de comando asociado con un vínculo en la ventana de alerta de escritorio.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|El texto que se muestra en la ventana de alerta de escritorio.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|El vínculo que se muestra en la ventana de alerta de escritorio.|

## <a name="remarks"></a>Comentarios

El `CMFCDesktopAlertWndInfo` clase se pasa a la [cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) método para especificar los elementos que se muestran en el cuadro de diálogo predeterminado de la ventana de alerta de escritorio. El cuadro de diálogo predeterminado puede contener tres elementos:

- Un icono que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Una etiqueta o un mensaje de texto, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Un vínculo, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Para establecer el comando que se ejecuta cuando se hace clic en el vínculo, llame a [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Si el cuadro de diálogo predeterminado no es suficiente, puede crear un cuadro de diálogo personalizado y páselo a la [cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) método en lugar de usar esta clase. Para obtener más información, consulte [CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar los diversos miembros de la `CMFCDesktopAlertWndInfo` clase. En el ejemplo se muestra cómo establecer el identificador del icono que se muestra, el texto que se muestra en la ventana de alerta de escritorio, el vínculo que se muestra en la ventana de alerta de escritorio y el identificador de comando que está asociado con un vínculo en la ventana de alerta de escritorio. Este ejemplo forma parte de la [ejemplo de demostración de alerta de escritorio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDesktopAlertDialog.h

##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator=

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parámetros

[in] *src*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon

Identificador del icono que se muestra.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID

El identificador de comando asociado con un vínculo en la ventana de alerta de escritorio.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Comentarios

El identificador de comando se envía al propietario de la ventana emergente cuando el usuario hace clic en el vínculo especificado por [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText

El texto que se muestra en la ventana de alerta de escritorio.

```
CString m_strText;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL

El vínculo que se muestra en la ventana de alerta de escritorio.

```
CString m_strURL;
```

### <a name="remarks"></a>Comentarios

Cuando el usuario hace clic en el vínculo, el comando que tiene el [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) identificador de comando que se enviarán al propietario de la ventana emergente.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd (clase)](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)
