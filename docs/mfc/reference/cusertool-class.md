---
title: Clase CUserTool | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserTool
dev_langs:
- C++
helpviewer_keywords:
- CUserTool class
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2e0b082be6aac7314d8251f89b42ed09e44e2f3d
ms.lasthandoff: 02/24/2017

---
# <a name="cusertool-class"></a>Clase CUserTool
Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa. El **herramientas** ficha de la **personalizar** cuadro de diálogo ( [CMFCToolBarsCustomizeDialog clase](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permite al usuario agregar herramientas de usuario y para especificar el nombre, comando, argumentos y el directorio inicial para cada herramienta de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dibuja el icono de la herramienta de usuario en un rectángulo determinado.|  
|[CUserTool::GetCommand](#getcommand)|Devuelve una cadena que contiene el texto del comando asociado con la herramienta de usuario.|  
|[CUserTool::GetCommandId](#getcommandid)|Devuelve el identificador de comando del elemento de menú de la herramienta de usuario.|  
|[CUserTool::Invoke](#invoke)|Ejecuta el comando asociado a la herramienta de usuario.|  
|[CUserTool::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo. (Invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CUserTool::SetCommand](#setcommand)|Establece el comando asociado con la herramienta de usuario.|  
|[CUserTool::SetToolIcon](#settoolicon)|Carga el icono de la herramienta de usuario de la aplicación asociada a la herramienta.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Carga el icono predeterminado para una herramienta de usuario.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Los argumentos de línea de comandos para la herramienta de usuario.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|El directorio inicial de la herramienta de usuario.|  
|[CUserTool::m_strLabel](#m_strlabel)|El nombre de la herramienta que se muestra en el elemento de menú de la herramienta.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de cómo habilitar las herramientas de usuario de la aplicación, consulte [CUserToolsManager clase](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear una herramienta de un `CUserToolsManager` objeto, establecer el `m_strLabel` variable miembro y establezca la aplicación que se ejecuta la herramienta de usuario. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#35;](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxusertool.h  
  
##  <a name="a-namecopyicontoclipboarda--cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawtoolicona--cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIcon  
 Dibuja el icono de la herramienta de usuario en el centro de un rectángulo especificado.  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectImage`  
 Especifica las coordenadas del área para mostrar el icono.  
  
##  <a name="a-namegetcommanda--cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand  
 Devuelve una cadena que contiene el texto del comando asociado con la herramienta de usuario.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a `CString` objeto que contiene el texto del comando asociado con la herramienta de usuario.  
  
##  <a name="a-namegetcommandida--cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId  
 Devuelve el identificador de comando de la herramienta de usuario.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando de esta herramienta de usuario.  
  
##  <a name="a-nameinvokea--cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Invoke  
 Ejecuta el comando asociado a la herramienta de usuario.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el comando se ejecutó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) para ejecutar un comando asociado con la herramienta de usuario. La función produce un error si el comando está vacío o si [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) se produce un error.  
  
##  <a name="a-nameloaddefaulticona--cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon  
 Carga el icono predeterminado para una herramienta de usuario.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el icono de cargando ( `HICON`), o `NULL` si no se puede cargar el icono predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando no puede cargar un icono para una herramienta definida por el usuario desde el archivo ejecutable de la herramienta.  
  
 Invalide este método para proporcionar su propio icono de la herramienta de forma predeterminada.  
  
##  <a name="a-namemstrargumentsa--cusertoolmstrarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments  
 Los argumentos de línea de comandos para la herramienta de usuario.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta cadena se pasa a la herramienta cuando se llama a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado con esta herramienta.  
  
##  <a name="a-namemstrinitialdirectorya--cusertoolmstrinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory  
 Especifica el directorio inicial de la herramienta de usuario.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable especifica el directorio inicial que se ejecuta la herramienta cuando se llama a [CUserTool::Invoke](#invoke) o cuando un usuario hace clic en el comando asociado con esta herramienta.  
  
##  <a name="a-namemstrlabela--cusertoolmstrlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel  
 La etiqueta que se muestra en el elemento de menú de la herramienta.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="a-nameserializea--cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcommanda--cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand  
 Establece la aplicación que se ejecuta la herramienta de usuario.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszCmd`  
 Especifica la nueva aplicación que se asociará con la herramienta de usuario.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer una nueva aplicación que se ejecuta la herramienta de usuario. El método destruye el icono antiguo y carga un nuevo icono de la aplicación dada. Si no puede cargar un icono de la aplicación, carga el icono predeterminado para una herramienta de usuario mediante una llamada a [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="a-namesettoolicona--cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::SetToolIcon  
 Carga el icono de la herramienta de usuario de la aplicación que utiliza la herramienta.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el icono de cargando.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para cargar el icono que se mostrará en el elemento de menú. Este método busca en el icono en el archivo ejecutable que utiliza la herramienta. Si no tiene un icono predeterminado, el icono proporcionado por [CUserTool::LoadDefaultIcon](#loaddefaulticon) se utiliza en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Clase CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)

