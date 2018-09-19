---
title: CUserTool (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 577e4b4e7bf54742035c8b4333d345ca894501ac
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708999"
---
# <a name="cusertool-class"></a>CUserTool (clase)
Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. El **herramientas** pestaña de la **personalizar** cuadro de diálogo ( [CMFCToolBarsCustomizeDialog (clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permite al usuario agregar herramientas de usuario y para especificar el nombre, comandos, argumentos, y directorio inicial para cada herramienta de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dibuja el icono de la herramienta de usuario en un rectángulo determinado.|  
|[CUserTool::GetCommand](#getcommand)|Devuelve una cadena que contiene el texto del comando asociado con la herramienta de usuario.|  
|[CUserTool::GetCommandId](#getcommandid)|Devuelve el identificador de comando del elemento de menú de la herramienta de usuario.|  
|[CUserTool::Invoke](#invoke)|Ejecuta el comando asociado con la herramienta de usuario.|  
|[CUserTool::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|  
|[CUserTool::SetCommand](#setcommand)|Establece el comando asociado con la herramienta de usuario.|  
|[CUserTool::SetToolIcon](#settoolicon)|Carga el icono de la herramienta de usuario de la aplicación asociada con la herramienta.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Carga el icono predeterminado para una herramienta de usuario.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Los argumentos de línea de comandos para la herramienta de usuario.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|El directorio inicial para la herramienta de usuario.|  
|[CUserTool::m_strLabel](#m_strlabel)|El nombre de herramienta que se muestra en el elemento de menú de la herramienta.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de cómo habilitar las herramientas de usuario en la aplicación, consulte [CUserToolsManager (clase)](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear una herramienta desde un `CUserToolsManager` de objetos, establezca el `m_strLabel` variable de miembro y establezca la aplicación que se ejecuta la herramienta de usuario. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard  
 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
  
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
[in] Un puntero a un contexto de dispositivo.  
  
*rectImage*<br/>
[in] Especifica las coordenadas del área para mostrar el icono.  
  
##  <a name="getcommand"></a>  CUserTool::GetCommand  
 Devuelve una cadena que contiene el texto del comando asociado con la herramienta de usuario.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a `CString` objeto que contiene el texto de comando asociado a la herramienta de usuario.  
  
##  <a name="getcommandid"></a>  CUserTool::GetCommandId  
 Devuelve el identificador de comando de la herramienta de usuario.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando de esta herramienta de usuario.  
  
##  <a name="invoke"></a>  CUserTool::Invoke  
 Ejecuta el comando asociado con la herramienta de usuario.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el comando se ejecutó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) para ejecutar un comando asociado con la herramienta de usuario. La función produce un error si el comando está vacío o si [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) se produce un error.  
  
##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon  
 Carga el icono predeterminado para una herramienta de usuario.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de la carga icono (HICON), o NULL si no se puede cargar el icono predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El marco llama a este método cuando no puede cargar un icono para una herramienta definido por el usuario desde el archivo ejecutable de la herramienta.  
  
 Invalide este método para proporcionar su propio icono de la herramienta de forma predeterminada.  
  
##  <a name="m_strarguments"></a>  CUserTool::m_strArguments  
 Los argumentos de línea de comandos para la herramienta de usuario.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta cadena se pasa a la herramienta cuando se llama a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado con esta herramienta.  
  
##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory  
 Especifica el directorio inicial para la herramienta de usuario.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable especifica el directorio inicial que se ejecuta la herramienta en al llamar a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado con esta herramienta.  
  
##  <a name="m_strlabel"></a>  CUserTool::m_strLabel  
 La etiqueta que se muestra en el elemento de menú de la herramienta.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>  CUserTool::Serialize  
 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *ar*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcommand"></a>  CUserTool::SetCommand  
 Establece la aplicación que se ejecuta la herramienta de usuario.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszCmd*<br/>
[in] Especifica la nueva aplicación va a asociar con la herramienta de usuario.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer una nueva aplicación que se ejecuta la herramienta de usuario. El método destruye el icono anterior y carga un nuevo icono de la aplicación dada. Si no puede cargar un icono de la aplicación, carga el icono predeterminado para una herramienta de usuario mediante una llamada a [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="settoolicon"></a>  CUserTool::SetToolIcon  
 Carga el icono de la herramienta de usuario de la aplicación que utiliza la herramienta.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el icono cargado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para cargar el icono que se mostrará en el elemento de menú. Este método busca en el icono en el archivo ejecutable que utiliza la herramienta. Si no tiene un icono predeterminado, el icono proporcionada por [CUserTool::LoadDefaultIcon](#loaddefaulticon) se usa en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager (clase)](../../mfc/reference/cusertoolsmanager-class.md)
