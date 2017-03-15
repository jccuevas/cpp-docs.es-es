---
title: Clase CCommandLineInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommandLineInfo
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo class
- command line, parsing
- parsing, command-line arguments
- argv argument
- startup code, parsing command-line arguments
- application flags [C++]
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: cb8cd58e4e7cf0318b8826cf473739e26e730273
ms.lasthandoff: 02/24/2017

---
# <a name="ccommandlineinfo-class"></a>Clase CCommandLineInfo
Ayuda a analizar la línea de comandos al iniciar la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construye un valor predeterminado `CCommandLineInfo` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::ParseParam](#parseparam)|Invalidar esta devolución de llamada para analizar los parámetros individuales.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Indica la línea de comandos **/automatización** se encontró la opción.|  
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Indica la línea de comandos **/incrustación** se encontró la opción.|  
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Indica si se debe mostrar una pantalla de presentación.|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Indica que el comando de shell para procesarse.|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Indica que el controlador de nombre si el comando de shell es imprimir; de lo contrario, está vacío.|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Indica el nombre de archivo se abren o se imprime; vacío si el comando de shell es nuevo o DDE.|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|Indica el puerto nombre si el comando de shell es imprimir; de lo contrario, está vacío.|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Indica la impresora nombre si el comando de shell es imprimir; de lo contrario, está vacío.|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Indica el identificador único de reinicio para el Administrador de reinicio si el Administrador de reinicio reinicia la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación MFC normalmente creará una instancia local de esta clase en el [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) función de su objeto de aplicación. Este objeto se pasa a continuación [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), que llama repetidamente a [ParseParam](#parseparam) para rellenar la `CCommandLineInfo` objeto. El `CCommandLineInfo` , a continuación, se pasa el objeto al [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) para controlar los argumentos de línea de comandos y las marcas.  
  
 Puede utilizar este objeto para encapsular las siguientes opciones de línea de comandos y parámetros:  
  
|Argumento de línea de comandos|Comando ejecutado|  
|----------------------------|----------------------|  
|*app*|Nuevo archivo.|  
|*aplicación* nombre de archivo|Abrir archivo.|  
|*aplicación* **/p** nombre de archivo|Archivo de impresión a la impresora predeterminada.|  
|*aplicación* **/pt** puerto de controlador de impresora de nombre de archivo|Archivo de impresión en la impresora especificada.|  
|*app* **/dde**|Inicie y await comando DDE.|  
|*aplicación*  ** /automatización**|Iniciar como un servidor de automatización OLE.|  
|*aplicación* **/ incrustación**|Inicio para editar un elemento OLE incrustado.|  
|*aplicación*  ** /Register**<br /><br /> *aplicación*  ** /regserver**|Informa a la aplicación para realizar las tareas de registro.|  
|*aplicación* **/ Unregister**<br /><br /> *aplicación* **/Unregserver**|Informa a la aplicación para realizar las tareas de anulación del registro.|  
  
 Derivar una nueva clase de `CCommandLineInfo` ante otros indicadores y valores de parámetro. Invalidar [ParseParam](#parseparam) ante las nuevas marcas.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameccommandlineinfoa--ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo  
 Este constructor crea un `CCommandLineInfo` objeto con valores predeterminados.  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado es mostrar la pantalla de presentación ( `m_bShowSplash` **= TRUE**) y para ejecutar el comando nuevo en el menú archivo ( `m_nShellCommand` **= NuevoArchivo**).  
  
 El marco de aplicación llama [ParseParam](#parseparam) para rellenar los miembros de datos de este objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#54;](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="a-namembrunautomateda--ccommandlineinfombrunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated  
 Indica que el **/automatización** marca no se encontró en la línea de comandos.  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si **TRUE**, esto significa que se inicie como un servidor de automatización OLE.  
  
##  <a name="a-namembrunembeddeda--ccommandlineinfombrunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded  
 Indica que el **/incrustación** marca no se encontró en la línea de comandos.  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si **TRUE**, esto significa el inicio de la edición de un elemento OLE incrustado.  
  
##  <a name="a-namembshowsplasha--ccommandlineinfombshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash  
 Indica que se debe mostrar la pantalla de presentación.  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si **TRUE**, esto significa que la pantalla de presentación para esta aplicación debería mostrarse durante el inicio. La implementación predeterminada de [ParseParam](#parseparam) este miembro de datos se establece en **TRUE** si [m_nShellCommand](#m_nshellcommand) es igual a **CCommandLineInfo::FileNew**.  
  
##  <a name="a-namemnshellcommanda--ccommandlineinfomnshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand  
 Indica que el comando de shell para esta instancia de la aplicación.  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo de este miembro de datos es el siguiente tipo enumerado se define en la `CCommandLineInfo` clase.  
  
 `enum{`  
  
 `FileNew,`  
  
 `FileOpen,`  
  
 `FilePrint,`  
  
 `FilePrintTo,`  
  
 `FileDDE,`  
  
 `AppRegister,`  
  
 `AppUnregister,`  
  
 `RestartByRestartManager,`  
  
 `FileNothing = -1`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores, consulte la lista siguiente.  
  
- `CCommandLineInfo::FileNew`Indica que no se encontró ningún nombre de archivo en la línea de comandos.  
  
- `CCommandLineInfo::FileOpen`Indica que se encontró un nombre de archivo en la línea de comandos y que ninguno de los indicadores siguientes se encontraron en la línea de comandos: `/p`, `/pt`, `/dde`.  
  
- `CCommandLineInfo::FilePrint`Indica que el `/p` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::FilePrintTo`Indica que el `/pt` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::FileDDE`Indica que el `/dde` marca no se encontró en la línea de comandos.  
  
- `CCommandLineInfo::AppRegister`Indica que el `/Register` o `/Regserver` marca se encontró en la línea de comandos y la aplicación ha solicitado que se registre.  
  
- `CCommandLineInfo::AppUnregister`Indica que el `/Unregister` o `/Unregserver` aplicación ha solicitado que se anule el registro.  
  
- `CCommandLineInfo::RestartByRestartManager`Indica que se ha reiniciado la aplicación mediante el Administrador de reinicio.  
  
- `CCommandLineInfo::FileNothing`Desactiva la presentación de una nueva ventana secundaria MDI en el inicio. Por diseño, aplicaciones MDI generados por el Asistente de la aplicación muestran una nueva ventana secundaria en el inicio. Para desactivar esta característica, puede usar una aplicación `CCommandLineInfo::FileNothing` que el comando de shell cuando llama a [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand`llama a la `InitInstance( )` de todos los `CWinApp` las clases derivadas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#55;](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="a-namemstrdrivernamea--ccommandlineinfomstrdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName  
 Almacena el valor del tercer parámetro no marca en la línea de comandos.  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este parámetro es el nombre del controlador de impresora para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece esta datos miembro si la **/pt** marca no se encontró en la línea de comandos.  
  
##  <a name="a-namemstrfilenamea--ccommandlineinfomstrfilename"></a><a name="m_strfilename"></a>CCommandLineInfo::m_strFileName  
 Almacena el valor del primer parámetro no marca en la línea de comandos.  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este parámetro es el nombre del archivo que desee abrir.  
  
##  <a name="a-namemstrportnamea--ccommandlineinfomstrportname"></a><a name="m_strportname"></a>CCommandLineInfo::m_strPortName  
 Almacena el valor del cuarto parámetro no marca en la línea de comandos.  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este parámetro es el nombre del puerto para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece esta datos miembro si la **/pt** marca no se encontró en la línea de comandos.  
  
##  <a name="a-namemstrprinternamea--ccommandlineinfomstrprintername"></a><a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName  
 Almacena el valor del segundo parámetro no marca en la línea de comandos.  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este parámetro es el nombre de la impresora para un comando de shell para la impresión. La implementación predeterminada de [ParseParam](#parseparam) establece esta datos miembro si la **/pt** marca no se encontró en la línea de comandos.  
  
##  <a name="a-namemstrrestartidentifiera--ccommandlineinfomstrrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier  
 El único reinicie identificador en la línea de comandos.  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>Comentarios  
 El identificador de reinicio es único para cada instancia de la aplicación.  
  
 Si el Administrador de reinicio sale de la aplicación y está configurado para reiniciarlo, el Administrador de reinicio ejecuta la aplicación desde la línea de comandos con el identificador de reinicio como un parámetro opcional. Cuando el Administrador de reinicio utiliza el identificador de reinicio, la aplicación puede volver a abrir los documentos abiertos previamente y recuperar los archivos guardados automáticamente.  
  
##  <a name="a-nameparseparama--ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam  
 El marco de trabajo llama a esta función para analizar/interpretar los parámetros individuales desde la línea de comandos. La segunda versión difiere de la primera sólo en proyectos de Unicode.  
  
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
 Indica si este es el último parámetro o marcador en la línea de comandos.  
  
### <a name="remarks"></a>Comentarios  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) llamadas `ParseParam` una vez para cada parámetro o una marca en la línea de comandos, pasando el argumento `pszParam`. Si el primer carácter del parámetro es un ' ** - **'o' ** / **', a continuación, se quita y *bFlag* está establecido en **TRUE**. Al analizar el parámetro final, `bLast` está establecido en **TRUE**.  
  
 La implementación predeterminada de esta función reconoce los siguientes indicadores: **/p**, **/pt**, **/dde**, **/automatización**, y **/incrustación**, como se muestra en la tabla siguiente:  
  
|Argumento de línea de comandos|Comando ejecutado|  
|----------------------------|----------------------|  
|*app*|Nuevo archivo.|  
|*aplicación* nombre de archivo|Abrir archivo.|  
|*aplicación* **/p** nombre de archivo|Archivo de impresión a la impresora predeterminada.|  
|*aplicación* **/pt** puerto de controlador de impresora de nombre de archivo|Archivo de impresión en la impresora especificada.|  
|*app* **/dde**|Inicie y await comando DDE.|  
|*aplicación*  ** /automatización**|Iniciar como un servidor de automatización OLE.|  
|*aplicación* **/ incrustación**|Inicio para editar un elemento OLE incrustado.|  
|*aplicación*  ** /Register**<br /><br /> *aplicación*  ** /regserver**|Informa a la aplicación para realizar las tareas de registro.|  
|*aplicación* **/ Unregister**<br /><br /> *aplicación* **/Unregserver**|Informa a la aplicación para realizar las tareas de anulación del registro.|  
  
 Esta información se almacena en [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), y [m_nShellCommand](#m_nshellcommand). Marcas están marcadas, ya sea por una barra diagonal ' ** / **'o guión' ** - **'.  
  
 La implementación predeterminada coloca el primer parámetro no marca en [m_strFileName](#m_strfilename). En el caso de la **/pt** marca, la implementación predeterminada coloca el segundo, tercer y cuarto parámetros no marca en [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), y [m_strPortName](#m_strportname), respectivamente.  
  
 La implementación predeterminada también establece [m_bShowSplash](#m_bshowsplash) a **TRUE** sólo en el caso de un nuevo archivo. En el caso de un nuevo archivo, el usuario ha realizado la acción que implica la propia aplicación. En cualquier otro caso, incluida la apertura de los archivos existentes con el shell, la acción de usuario implica el archivo directamente. En el punto de vista centrado en documentos, no necesario anunciar la aplicación a partir la pantalla de presentación.  
  
 Reemplace esta función en su clase derivada para administrar otros valores de parámetro y marca.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)


