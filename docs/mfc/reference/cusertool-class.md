---
title: Clase CUserTool
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502246"
---
# <a name="cusertool-class"></a>Clase CUserTool

Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. La pestaña **herramientas** del cuadro de diálogo **personalizar** ( [clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permite al usuario agregar herramientas de usuario y especificar el nombre, el comando, los argumentos y el directorio inicial para cada herramienta de usuario.

## <a name="syntax"></a>Sintaxis

```
class CUserTool : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dibuja el icono de la herramienta de usuario en un rectángulo especificado.|
|[CUserTool::GetCommand](#getcommand)|Devuelve una cadena que contiene el texto del comando asociado a la herramienta de usuario.|
|[CUserTool::GetCommandId](#getcommandid)|Devuelve el identificador de comando del elemento de menú de la herramienta de usuario.|
|[CUserTool::Invoke](#invoke)|Ejecuta el comando asociado a la herramienta de usuario.|
|[CUserTool::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|
|[CUserTool::SetCommand](#setcommand)|Establece el comando asociado a la herramienta de usuario.|
|[CUserTool::SetToolIcon](#settoolicon)|Carga el icono de la herramienta de usuario desde la aplicación asociada a la herramienta.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Carga el icono predeterminado para una herramienta de usuario.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumentos de la línea de comandos para la herramienta de usuario.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Directorio inicial de la herramienta de usuario.|
|[CUserTool::m_strLabel](#m_strlabel)|Nombre de la herramienta que se muestra en el elemento de menú de la herramienta.|

## <a name="remarks"></a>Comentarios

Para obtener más información sobre cómo habilitar las herramientas de usuario en la aplicación, consulte [clase CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear una herramienta a `CUserToolsManager` partir de un objeto `m_strLabel` , establecer la variable miembro y establecer la aplicación que ejecuta la herramienta de usuario. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxusertool. h

##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon

Dibuja el icono de la herramienta de usuario en el centro de un rectángulo especificado.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rectImage*<br/>
de Especifica las coordenadas del área para mostrar el icono.

##  <a name="getcommand"></a>  CUserTool::GetCommand

Devuelve una cadena que contiene el texto del comando asociado a la herramienta de usuario.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a `CString` un objeto que contiene el texto del comando asociado a la herramienta de usuario.

##  <a name="getcommandid"></a>  CUserTool::GetCommandId

Devuelve el identificador de comando de la herramienta de usuario.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de comando de esta herramienta de usuario.

##  <a name="invoke"></a>  CUserTool::Invoke

Ejecuta el comando asociado a la herramienta de usuario.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el comando se ejecutó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llama a [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) para ejecutar un comando asociado a la herramienta de usuario. Se produce un error en la función si el comando está vacío o si se produce un error en [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) .

##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon

Carga el icono predeterminado para una herramienta de usuario.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono de carga (HICON) o NULL si no se puede cargar el icono predeterminado.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando no puede cargar un icono para una herramienta definida por el usuario desde el archivo ejecutable de la herramienta.

Invalide este método para proporcionar su propio icono de herramienta predeterminada.

##  <a name="m_strarguments"></a>  CUserTool::m_strArguments

Argumentos de la línea de comandos para la herramienta de usuario.

```
CString m_strArguments;
```

### <a name="remarks"></a>Comentarios

Esta cadena se pasa a la herramienta cuando se llama a [CUserTool:: Invoke](#invoke) o cuando un usuario hace clic en el comando asociado a esta herramienta.

##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory

Especifica el directorio inicial de la herramienta de usuario.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Comentarios

Esta variable especifica el directorio inicial en el que se ejecuta la herramienta cuando se llama a [CUserTool:: Invoke](#invoke) o cuando un usuario hace clic en el comando asociado a esta herramienta.

##  <a name="m_strlabel"></a>  CUserTool::m_strLabel

La etiqueta que se muestra en el elemento de menú de la herramienta.

```
CString m_strLabel;
```

##  <a name="serialize"></a>  CUserTool::Serialize

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

de *ar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setcommand"></a>  CUserTool::SetCommand

Establece la aplicación que ejecuta la herramienta de usuario.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parámetros

*lpszCmd*<br/>
de Especifica la nueva aplicación que se va a asociar a la herramienta de usuario.

### <a name="remarks"></a>Comentarios

Llame a este método para establecer una nueva aplicación que ejecute la herramienta de usuario. El método destruye el icono anterior y carga un nuevo icono de la aplicación especificada. Si no puede cargar un icono de la aplicación, carga el icono predeterminado de una herramienta de usuario mediante una llamada a [CUserTool:: LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>  CUserTool::SetToolIcon

Carga el icono de la herramienta de usuario de la aplicación que utiliza la herramienta.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono cargado.

### <a name="remarks"></a>Comentarios

Llame a este método para cargar el icono que se va a mostrar en el elemento de menú. Este método busca el icono en el archivo ejecutable que utiliza la herramienta. Si no tiene un icono predeterminado, se utiliza en su lugar el icono proporcionado por [CUserTool:: LoadDefaultIcon](#loaddefaulticon) .

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager (clase)](../../mfc/reference/cusertoolsmanager-class.md)
