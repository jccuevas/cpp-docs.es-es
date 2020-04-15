---
title: CCommandLineInfo (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369463"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo (clase)

Ayuda a analizar la línea de comandos al iniciar la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Construye un `CCommandLineInfo` objeto predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Invalide esta devolución de llamada para analizar parámetros individuales.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Indica que se `/Automation` ha encontrado la opción de línea de comandos.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Indica que se `/Embedding` ha encontrado la opción de línea de comandos.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Indica si se debe mostrar una pantalla de presentación.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Indica el comando shell que se va a procesar.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Indica el nombre del controlador si el comando shell es Imprimir en; vacío.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Indica el nombre de archivo que se va a abrir o imprimir; vacío si el comando shell es New o DDE.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Indica el nombre del puerto si el comando shell es Imprimir en; vacío.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Indica el nombre de la impresora si el comando de shell es Imprimir en; vacío.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Indica el identificador de reinicio único para el administrador de reinicio si el administrador de reinicio reinicia la aplicación.|

## <a name="remarks"></a>Observaciones

Una aplicación MFC normalmente creará una instancia local de esta clase en la función [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de su objeto de aplicación. A continuación, este objeto se pasa a [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), `CCommandLineInfo` que llama repetidamente a [ParseParam](#parseparam) para rellenar el objeto. A `CCommandLineInfo` continuación, el objeto se pasa a [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) para controlar los argumentos de línea de comandos y los indicadores.

Puede utilizar este objeto para encapsular las siguientes opciones y parámetros de línea de comandos:

|Argumento de línea de comandos|Comando ejecutado|
|----------------------------|----------------------|
|*app*|Nuevo archivo.|
|nombre de archivo de la *aplicación*|Abra el archivo.|
|nombre de archivo de la *aplicación* `/p`|Imprima el archivo en la impresora predeterminada.|
|puerto del controlador de impresora del nombre de archivo de la *aplicación* `/pt`|Imprima el archivo en la impresora especificada.|
|*app* `/dde`|Inicie y espere el comando DDE.|
|*app* `/Automation`|Iniciar como un servidor de automatización OLE.|
|*app* `/Embedding`|Inicie para editar un elemento OLE incrustado.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informa a la aplicación para realizar cualquier tarea de registro.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informa a la aplicación para realizar cualquier tarea de cancelación de registro.|

Derive una nueva `CCommandLineInfo` clase de para controlar otros indicadores y valores de parámetro. Invalide [ParseParam](#parseparam) para controlar las nuevas marcas.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo

Este constructor `CCommandLineInfo` crea un objeto con valores predeterminados.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Observaciones

El valor predeterminado es mostrar `m_bShowSplash=TRUE`la pantalla de presentación ( ) `m_nShellCommand`y ejecutar el comando Nuevo en el menú Archivo ( **.**

El marco de trabajo de la aplicación llama a [ParseParam](#parseparam) para rellenar los miembros de datos de este objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated

Indica que `/Automation` la marca se ha encontrado en la línea de comandos.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, esto significa iniciarse como un servidor de automatización OLE.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded

Indica que `/Embedding` la marca se ha encontrado en la línea de comandos.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, esto significa iniciar para editar un elemento OLE incrustado.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash

Indica que se debe mostrar la pantalla de presentación.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, esto significa que la pantalla de presentación de esta aplicación debe mostrarse durante el inicio. La implementación predeterminada de [ParseParam](#parseparam) establece [m_nShellCommand](#m_nshellcommand) este miembro `CCommandLineInfo::FileNew`de datos en TRUE si m_nShellCommand es igual a .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand

Indica el comando shell para esta instancia de la aplicación.

```
m_nShellCommand;
```

### <a name="remarks"></a>Observaciones

El tipo de este miembro de datos es el `CCommandLineInfo` siguiente tipo enumerado, que se define en la clase.

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

Para obtener una breve descripción de estos valores, consulte la lista siguiente.

- `CCommandLineInfo::FileNew`Indica que no se ha encontrado ningún nombre de archivo en la línea de comandos.

- `CCommandLineInfo::FileOpen`Indica que se ha encontrado un nombre de archivo en la línea de `/p`comandos y que no se encontró ninguna de las siguientes marcas en la línea de comandos: , `/pt`, `/dde`.

- `CCommandLineInfo::FilePrint`Indica que `/p` la marca se ha encontrado en la línea de comandos.

- `CCommandLineInfo::FilePrintTo`Indica que `/pt` la marca se ha encontrado en la línea de comandos.

- `CCommandLineInfo::FileDDE`Indica que `/dde` la marca se ha encontrado en la línea de comandos.

- `CCommandLineInfo::AppRegister`Indica que `/Register` se `/Regserver` ha encontrado la marca o en la línea de comandos y se ha pedido a la aplicación que se registre.

- `CCommandLineInfo::AppUnregister`Indica que `/Unregister` se `/Unregserver` ha pedido que se anule el registro de la aplicación.

- `CCommandLineInfo::RestartByRestartManager`Indica que el Administrador de reinicio ha reiniciado la aplicación.

- `CCommandLineInfo::FileNothing`Desactiva la visualización de una nueva ventana secundaria MDI al iniciarse. Por diseño, las aplicaciones MDI generadas por el Asistente para aplicaciones muestran una nueva ventana secundaria al inicio. Para desactivar esta característica, una `CCommandLineInfo::FileNothing` aplicación puede usar la aplicación como comando shell cuando llama a [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand`es llamado `InitInstance( )` por `CWinApp` todas las clases derivadas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName

Almacena el valor del tercer parámetro que no es de marca en la línea de comandos.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Observaciones

Este parámetro suele ser el nombre del controlador de impresora para un comando Imprimir en shell. La implementación predeterminada de [ParseParam](#parseparam) establece `/pt` este miembro de datos solo si el indicador se encontró en la línea de comandos.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLineInfo::m_strFileName

Almacena el valor del primer parámetro que no es de marca en la línea de comandos.

```
CString m_strFileName;
```

### <a name="remarks"></a>Observaciones

Este parámetro suele ser el nombre del archivo que se va a abrir.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLineInfo::m_strPortName

Almacena el valor del cuarto parámetro que no es de marca en la línea de comandos.

```
CString m_strPortName;
```

### <a name="remarks"></a>Observaciones

Este parámetro suele ser el nombre del puerto de impresora para un comando Imprimir en shell. La implementación predeterminada de [ParseParam](#parseparam) establece `/pt` este miembro de datos solo si el indicador se encontró en la línea de comandos.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName

Almacena el valor del segundo parámetro que no es de marca en la línea de comandos.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Observaciones

Este parámetro suele ser el nombre de la impresora para un comando Imprimir en shell. La implementación predeterminada de [ParseParam](#parseparam) establece `/pt` este miembro de datos solo si el indicador se encontró en la línea de comandos.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier

Identificador de reinicio único en la línea de comandos.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Observaciones

El identificador de reinicio es único para cada instancia de la aplicación.

Si el administrador de reinicio sale de la aplicación y está configurado para reiniciarla, el administrador de reinicio ejecuta la aplicación desde la línea de comandos con el identificador de reinicio como parámetro opcional. Cuando el administrador de reinicio utiliza el identificador de reinicio, la aplicación puede volver a abrir los documentos abiertos previamente y recuperar archivos guardados automáticamente.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam

El marco de trabajo llama a esta función para analizar e interpretar parámetros individuales desde la línea de comandos. La segunda versión difiere de la primera solo en proyectos Unicode.

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

*pszParam*<br/>
El parámetro o la marca.

*bFlag*<br/>
Indica si *pszParam* es un parámetro o una marca.

*Explosión*<br/>
Indica si este es el último parámetro o indicador en la línea de comandos.

### <a name="remarks"></a>Observaciones

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) `ParseParam` llama una vez para cada parámetro o marca en la línea de comandos, pasando el argumento a *pszParam*. Si el primer carácter del **-** parámetro es **/** un ' ' o un ' ', entonces se quita y *bFlag* se establece en TRUE. Al analizar el parámetro final, *bLast* se establece en TRUE.

La implementación predeterminada de esta función `/dde`reconoce `/Automation`los `/Embedding`siguientes indicadores: `/p`, `/pt`, , , , , , como se muestra en la tabla siguiente:

|Argumento de línea de comandos|Comando ejecutado|
|----------------------------|----------------------|
|*app*|Nuevo archivo.|
|nombre de archivo de la *aplicación*|Abra el archivo.|
|nombre de archivo de la *aplicación* `/p`|Imprima el archivo en la impresora predeterminada.|
|puerto del controlador de impresora del nombre de archivo de la *aplicación* `/pt`|Imprima el archivo en la impresora especificada.|
|*app* `/dde`|Inicie y espere el comando DDE.|
|*app* `/Automation`|Iniciar como un servidor de automatización OLE.|
|*app* `/Embedding`|Inicie para editar un elemento OLE incrustado.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informa a la aplicación para realizar cualquier tarea de registro.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informa a la aplicación para realizar cualquier tarea de cancelación de registro.|

Esta información se almacena en [m_bRunAutomated,](#m_brunautomated) [m_bRunEmbedded](#m_brunembedded)y [m_nShellCommand](#m_nshellcommand). Las marcas se marcan con **/** una barra diagonal **-**' ' o guion ' '.

La implementación predeterminada coloca el primer parámetro que no es de marca en [m_strFileName](#m_strfilename). En el caso `/pt` de la marca, la implementación predeterminada coloca el segundo, tercer y cuarto parámetros que no son de marca en [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)y [m_strPortName](#m_strportname), respectivamente.

La implementación predeterminada también establece [m_bShowSplash](#m_bshowsplash) en TRUE solo en el caso de un nuevo archivo. En el caso de un nuevo archivo, el usuario ha tomado medidas que implican la propia aplicación. En cualquier otro caso, incluida la apertura de archivos existentes mediante el shell, la acción del usuario implica el archivo directamente. En un punto de vista centrado en el documento, la pantalla de presentación no necesita anunciar la inicio de la aplicación.

Invalide esta función en la clase derivada para controlar otros valores de marca y parámetro.

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
