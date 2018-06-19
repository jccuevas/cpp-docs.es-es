---
title: Clase CCommandLineInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43bd8f7b12eee847fd6b8784d21f4b565c7fc6a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357020"
---
# <a name="ccommandlineinfo-class"></a>Clase CCommandLineInfo
Ayuda a analizar la línea de comandos al iniciar la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construye un valor predeterminado `CCommandLineInfo` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::ParseParam](#parseparam)|Invalidar esta devolución de llamada para analizar los parámetros individuales.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Indica la línea de comandos `/Automation` se encontró la opción.|  
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Indica la línea de comandos `/Embedding` se encontró la opción.|  
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Indica si se debe mostrar una pantalla de presentación.|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Indica que el comando de shell para procesarse.|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Indica que el controlador de nombre, si el comando de shell es imprimir a; en caso contrario, está vacía.|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Indica el nombre de archivo se abre o se imprima; vacía si el comando de shell es nuevo o DDE.|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|Indica el puerto de nombre, si el comando de shell es imprimir a; en caso contrario, está vacía.|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Indica la impresora nombre si el comando de shell es imprimir a; en caso contrario, está vacía.|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Indica el identificador único de reinicio para el Administrador de reinicio si el Administrador de reinicio reinicia la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación MFC normalmente crea una instancia local de esta clase en el [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) función de su objeto de aplicación. Este objeto se pasa a continuación [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), que llama repetidamente [ParseParam](#parseparam) para rellenar la `CCommandLineInfo` objeto. El `CCommandLineInfo` , a continuación, se pasa el objeto a [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) para controlar los argumentos de línea de comandos y marcas.  
  
 Puede usar este objeto para encapsular las siguientes opciones de línea de comandos y parámetros:  
  
|Argumento de línea de comandos|Comando ejecutado|  
|----------------------------|----------------------|  
|*app*|Nuevo archivo.|  
|*aplicación* nombre de archivo|Archivos abiertos.|  
|*aplicación* `/p` nombre de archivo|Archivo de impresión a la impresora predeterminada.|  
|*aplicación* `/pt` puerto de controlador de impresora de nombre de archivo|Archivo de impresión a la impresora especificada.|  
|*Aplicación* `/dde`|Se inician y await comando DDE.|  
|*Aplicación* `/Automation`|Se inician como un servidor de automatización OLE.|  
|*Aplicación* `/Embedding`|Se inician editar un elemento OLE incrustado.|  
|*Aplicación* `/Register`<br /><br /> *Aplicación* `/Regserver`|Informa a la aplicación para realizar las tareas de registro.|  
|*Aplicación* `/Unregister`<br /><br /> *Aplicación* `/Unregserver`|Informa a la aplicación para realizar cualquier tarea de eliminación de registro.|  
  
 Derive una nueva clase de `CCommandLineInfo` para controlar otras marcas y los valores de parámetro. Invalidar [ParseParam](#parseparam) para controlar las marcas de nuevo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo  
 Este constructor crea un `CCommandLineInfo` objeto con valores predeterminados.  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado es mostrar la pantalla de presentación ( `m_bShowSplash=TRUE`) y para ejecutar el comando nuevo en el menú archivo ( `m_nShellCommand` **= NewFile**).  
  
 La aplicación framework llama [ParseParam](#parseparam) para rellenar los miembros de datos de este objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated  
 Indica que el `/Automation` marca no se encontró en la línea de comandos.  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, esto significa que se inician como un servidor de automatización OLE.  
  
##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded  
 Indica que el `/Embedding` marca no se encontró en la línea de comandos.  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, esto significa que se inician para editar un elemento OLE incrustado.  
  
##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash  
 Indica que se debe mostrar la pantalla de presentación.  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, esto significa que la pantalla de presentación para esta aplicación debe mostrarse durante el inicio. La implementación predeterminada de [ParseParam](#parseparam) este miembro de datos se establece en `TRUE` si [m_nShellCommand](#m_nshellcommand) es igual a `CCommandLineInfo::FileNew`.  
  
##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand  
 Indica que el comando de shell para esta instancia de la aplicación.  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo de este miembro de datos es el tipo enumerado siguiente, que se define en la `CCommandLineInfo` clase.  
  
```  
enum {  
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1  
    };  
```  
  
 Para obtener una breve descripción de estos valores, vea la siguiente lista.  
  
- `CCommandLineInfo::FileNew` Indica que no se encontró ningún nombre de archivo en la línea de comandos.  
  
- `CCommandLineInfo::FileOpen` Indica que se encontró un nombre de archivo en la línea de comandos y que ninguno de los indicadores siguientes se encuentra en la línea de comandos: `/p`, `/pt`, `/dde`.  
  
- `CCommandLineInfo::FilePrint` Indica que el `/p` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::FilePrintTo` Indica que el `/pt` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::FileDDE` Indica que el `/dde` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::AppRegister` Indica que la `/Register` o `/Regserver` marca no se encontró en la línea de comandos y se solicita a registrar la aplicación.  
  
- `CCommandLineInfo::AppUnregister` Indica que la `/Unregister` o `/Unregserver` se solicita a anular el registro de aplicación.  
  
- `CCommandLineInfo::RestartByRestartManager` Indica que la aplicación se reinició por el Administrador de reinicio.  
  
- `CCommandLineInfo::FileNothing` Desactiva la presentación de una nueva ventana secundaria MDI en el inicio. De forma predeterminada, las aplicaciones MDI generados por el Asistente de la aplicación muestran una nueva ventana secundaria al iniciarse. Para desactivar esta característica, puede usar una aplicación `CCommandLineInfo::FileNothing` que el comando de shell cuando llama a [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` llama a la `InitInstance( )` de todos los `CWinApp` las clases derivadas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName  
 Almacena el valor del tercer parámetro no marca en la línea de comandos.  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este parámetro normalmente es el nombre del controlador de impresora para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece este si solo del miembro de datos el `/pt` marca no se encontró en la línea de comandos.  
  
##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName  
 El valor del primer parámetro de marca no se almacena en la línea de comandos.  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este parámetro es el nombre del archivo que se abre.  
  
##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName  
 Almacena el valor del cuarto parámetro no marca en la línea de comandos.  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este parámetro normalmente es el nombre del puerto de impresora para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece este si solo del miembro de datos el `/pt` marca no se encontró en la línea de comandos.  
  
##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName  
 El valor del segundo parámetro de marca no se almacena en la línea de comandos.  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este parámetro normalmente es el nombre de la impresora para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece este si solo del miembro de datos el `/pt` marca no se encontró en la línea de comandos.  
  
##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier  
 El único reinicie identificador en la línea de comandos.  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>Comentarios  
 El identificador de reinicio es único para cada instancia de la aplicación.  
  
 Si el Administrador de reinicio sale de la aplicación y está configurado para reiniciar, el Administrador de reinicio ejecuta la aplicación desde la línea de comandos con el identificador de reinicio como un parámetro opcional. Cuando el Administrador de reinicio usa el identificador de reinicio, la aplicación puede volver a abrir los documentos abiertos previamente y recuperar archivos de autoguardado.  
  
##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam  
 El marco de trabajo llama a esta función para el análisis/interpretar los parámetros individuales desde la línea de comandos. La segunda versión es distinto del primero solo en los proyectos de Unicode.  
  
```  
virtual void ParseParam(
    const char* pszParam,  
    BOOL bFlag,  
    BOOL bLast);

 
virtual void ParseParam(
    const TCHAR* pszParam,  
    BOOL bFlag,  
    BOOL bLast);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszParam`  
 El parámetro o el indicador.  
  
 *bFlag*  
 Indica si `pszParam` es un parámetro o una marca.  
  
 `bLast`  
 Indica si se trata del último parámetro o marca en la línea de comandos.  
  
### <a name="remarks"></a>Comentarios  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) llamadas `ParseParam` una vez para cada parámetro o una marca en la línea de comandos, pase el argumento para `pszParam`. Si el primer carácter del parámetro es un ' **-**'o' **/**', a continuación, se quita y *bFlag* está establecido en `TRUE`. Al analizar el parámetro final, `bLast` está establecido en `TRUE`.  
  
 La implementación predeterminada de esta función reconoce los siguientes indicadores: `/p`, `/pt`, `/dde`, `/Automation`, y `/Embedding`, tal y como se muestra en la tabla siguiente:  
  
|Argumento de línea de comandos|Comando ejecutado|  
|----------------------------|----------------------|  
|*app*|Nuevo archivo.|  
|*aplicación* nombre de archivo|Archivos abiertos.|  
|*aplicación* `/p` nombre de archivo|Archivo de impresión a la impresora predeterminada.|  
|*aplicación* `/pt` puerto de controlador de impresora de nombre de archivo|Archivo de impresión a la impresora especificada.|  
|*Aplicación* `/dde`|Se inician y await comando DDE.|  
|*Aplicación* `/Automation`|Se inician como un servidor de automatización OLE.|  
|*Aplicación* `/Embedding`|Se inician editar un elemento OLE incrustado.|  
|*Aplicación* `/Register`<br /><br /> *Aplicación* `/Regserver`|Informa a la aplicación para realizar las tareas de registro.|  
|*Aplicación* `/Unregister`<br /><br /> *Aplicación* `/Unregserver`|Informa a la aplicación para realizar cualquier tarea de eliminación de registro.|  
  
 Esta información se almacena en [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), y [m_nShellCommand](#m_nshellcommand). Marcas se marcan, ya sea por una barra diagonal ' **/**'o guión' **-**'.  
  
 La implementación predeterminada hace que el primer parámetro de marca no en [m_strFileName](#m_strfilename). En el caso de los `/pt` marca, la implementación predeterminada hace que el segundo, tercer y cuarto parámetros no marca en [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), y [m_ strPortName](#m_strportname), respectivamente.  
  
 La implementación predeterminada también establece [m_bShowSplash](#m_bshowsplash) a `TRUE` sólo en el caso de un nuevo archivo. En el caso de un nuevo archivo, el usuario ha realizado la acción que implica la propia aplicación. En cualquier otro caso, incluida la apertura de archivos existentes mediante el shell, la acción de usuario implica el archivo directamente. En un punto de vista centrada en el documento, no necesario anunciar la aplicación de inicio de la pantalla de presentación.  
  
 Reemplace esta función en una clase derivada para controlar otros valores de marca y los parámetros.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

