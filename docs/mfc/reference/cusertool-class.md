---
title: CUserTool (clase)
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
ms.openlocfilehash: 183b30961e4a7d3079fa0d035a4ddc38bc2eebac
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752021"
---
# <a name="cusertool-class"></a>CUserTool (clase)

Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. La pestaña **Herramientas** del cuadro de diálogo **Personalizar** ( [CMFCToolBarsCustomizeDialog (Clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)permite al usuario agregar herramientas de usuario y especificar el nombre, el comando, los argumentos y el directorio inicial de cada herramienta de usuario.

## <a name="syntax"></a>Sintaxis

```
class CUserTool : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
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

|Nombre|Descripción|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Carga el icono predeterminado de una herramienta de usuario.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Los argumentos de línea de comandos para la herramienta de usuario.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|El directorio inicial de la herramienta de usuario.|
|[CUserTool::m_strLabel](#m_strlabel)|El nombre de la herramienta que se muestra en el elemento de menú de la herramienta.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de cómo habilitar las herramientas de usuario en la aplicación, vea [CUserToolsManager (Clase)](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CUserToolsManager` cómo crear `m_strLabel` una herramienta a partir de un objeto, establecer la variable miembro y establecer la aplicación que ejecuta la herramienta de usuario. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIcon

Dibuja el icono de la herramienta de usuario en el centro de un rectángulo especificado.

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectImage*<br/>
[en] Especifica las coordenadas del área para mostrar el icono.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand

Devuelve una cadena que contiene el texto del comando asociado a la herramienta de usuario.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al `CString` objeto que contiene el texto del comando asociado a la herramienta de usuario.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId

Devuelve el identificador de comando de la herramienta de usuario.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de comando de esta herramienta de usuario.

## <a name="cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Invoke

Ejecuta el comando asociado a la herramienta de usuario.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando se ejecutó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llama a [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) para ejecutar un comando asociado a la herramienta de usuario. Se produce un error en la función si el comando está vacío o si [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) produce un error.

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

Carga el icono predeterminado de una herramienta de usuario.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono cargado ( HICON) o NULL si no se puede cargar el icono predeterminado.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando no puede cargar un icono para una herramienta definida por el usuario desde el archivo ejecutable de la herramienta.

Invalide este método para proporcionar su propio icono de herramienta predeterminado.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments

Los argumentos de línea de comandos para la herramienta de usuario.

```
CString m_strArguments;
```

### <a name="remarks"></a>Observaciones

Esta cadena se pasa a la herramienta cuando se llama a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado a esta herramienta.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Especifica el directorio inicial de la herramienta de usuario.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Observaciones

Esta variable especifica el directorio inicial en el que se ejecuta la herramienta cuando se llama a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado a esta herramienta.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel

La etiqueta que se muestra en el elemento de menú de la herramienta.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serialize

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

[en] *ar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand

Establece la aplicación que ejecuta la herramienta de usuario.

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parámetros

*lpszCmd*<br/>
[en] Especifica la nueva aplicación que se asociará a la herramienta de usuario.

### <a name="remarks"></a>Observaciones

Llame a este método para establecer una nueva aplicación que se ejecuta la herramienta de usuario. El método destruye el icono antiguo y carga un nuevo icono de la aplicación dada. Si no puede cargar un icono desde la aplicación, carga el icono predeterminado para una herramienta de usuario llamando a [CUserTool::LoadDefaultIcon](#loaddefaulticon).

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::SetToolIcon

Carga el icono de la herramienta de usuario desde la aplicación que utiliza la herramienta.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Valor devuelto

Un identificador del icono cargado.

### <a name="remarks"></a>Observaciones

Llame a este método para cargar el icono que se mostrará en el elemento de menú. Este método busca el icono en el archivo ejecutable que utiliza la herramienta. Si no tiene un icono predeterminado, se utiliza en su lugar el icono proporcionado por [CUserTool::LoadDefaultIcon.](#loaddefaulticon)

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Clase CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
