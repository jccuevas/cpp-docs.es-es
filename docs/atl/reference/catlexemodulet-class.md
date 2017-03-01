---
title: Clase CAtlExeModuleT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlExeModuleT<T>
- CAtlExeModuleT
- ATL.CAtlExeModuleT<T>
- ATL::CAtlExeModuleT
- ATL.CAtlExeModuleT
dev_langs:
- C++
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 24ee6c4dfb13c31377bdd7d4f57a92d4f11ad4b8
ms.lasthandoff: 02/24/2017

---
# <a name="catlexemodulet-class"></a>Clase de CAtlExeModuleT
Esta clase representa el módulo de una aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CAtlExeModuleT`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|El constructor.|  
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[A CAtlExeModuleT:: InitializeCom](#initializecom)|Inicializa COM.|  
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analiza la línea de comandos y realiza el registro, si es necesario.|  
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Este método se llama inmediatamente después de que se sale del bucle de mensaje.|  
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Este método se llama inmediatamente antes de entrar en el bucle de mensajes.|  
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Registra el objeto de clase.|  
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Revoca el objeto de clase.|  
|[CAtlExeModuleT::Run](#run)|Este método se ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y limpiar.|  
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Este método ejecuta el bucle de mensajes.|  
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Anula COM.|  
|[CAtlExeModuleT::Unlock](#unlock)|Reduce el recuento de bloqueos del módulo.|  
|[CAtlExeModuleT::WinMain](#winmain)|Este método implementa el código necesario para ejecutar un archivo EXE.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Marca que indica que debe haber un retraso que se va a cerrar el módulo.|  
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Un valor de pausa utilizado para asegurarse de que todos los objetos se liberan antes del apagado.|  
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Un valor de tiempo de espera que se usa para retrasar la descarga del módulo.|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlExeModuleT`representa el módulo de una aplicación (EXE) y contiene código que admita la creación de un archivo EXE, la línea de comandos de procesamiento, el registro de objetos de clase, ejecuta el bucle de mensajes y limpiar en la salida.  
  
 Esta clase está diseñada para mejorar el rendimiento cuando los objetos COM en el servidor EXE continuamente se crean y destruyen. Una vez que se libera el último objeto COM, el archivo EXE espera durante un tiempo especificado por el [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) miembro de datos. Si no hay ninguna actividad durante este período (es decir, se crean los objetos COM), se inicia el proceso de cierre.  
  
 El [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) miembro de datos es un indicador que se utiliza para determinar si el archivo ejecutable debe usar el mecanismo definido anteriormente. Si se establece en false, el módulo se cerrará inmediatamente.  
  
 Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-namecatlexemoduleta--catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT  
 El constructor.  
  
```
CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no se pudo inicializar el módulo del archivo EXE, WinMain devolverá inmediatamente sin más procesamiento.  
  
##  <a name="a-namedtora--catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT  
 Destructor.  
  
```
~CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="a-nameinitializecoma--catlexemoduletinitializecom"></a><a name="initializecom"></a>A CAtlExeModuleT:: InitializeCom  
 Inicializa COM.  
  
```
static HRESULT InitializeCom() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama desde el constructor y se puede invalidar para inicializar el objeto COM de una manera diferente de la implementación predeterminada. La implementación predeterminada llama bien **CoInitializeEx (NULL, COINIT_MULTITHREADED)** o **CoInitialize(NULL)** según la configuración del proyecto.  
  
 Invalidación de este método normalmente es necesario reemplazar [CAtlExeModuleT::UninitializeCom](#uninitializecom).  
  
##  <a name="a-namembdelayshutdowna--catlexemoduletmbdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown  
 Marca que indica que debe haber un retraso que se va a cerrar el módulo.  
  
```
bool m_bDelayShutdown;
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte la [CAtlExeModuleT Introducción](../../atl/reference/catlexemodulet-class.md) para obtener más información.  
  
##  <a name="a-namemdwpausea--catlexemoduletmdwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause  
 Un valor de pausa utilizado para asegurarse de que todos los objetos ha desaparecido antes del apagado.  
  
```
DWORD m_dwPause;
```  
  
### <a name="remarks"></a>Comentarios  
 Cambie este valor después de llamar a [a CAtlExeModuleT:: InitializeCom](#initializecom) para establecer el número de milisegundos que se utiliza como el valor de pausa para apagar el servidor. El valor predeterminado es 1000 milisegundos.  
  
##  <a name="a-namemdwtimeouta--catlexemoduletmdwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut  
 Un valor de tiempo de espera que se usa para retrasar la descarga del módulo.  
  
```
DWORD m_dwTimeOut;
```  
  
### <a name="remarks"></a>Comentarios  
 Cambie este valor después de llamar a [a CAtlExeModuleT:: InitializeCom](#initializecom) para definir el número de milisegundos que se utiliza como el valor de tiempo de espera para cerrar el servidor. El valor predeterminado es 5000 milisegundos. Consulte la [CAtlExeModuleT Introducción](../../atl/reference/catlexemodulet-class.md) para obtener más detalles.  
  
##  <a name="a-nameparsecommandlinea--catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine  
 Analiza la línea de comandos y realiza el registro, si es necesario.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpCmdLine`  
 La línea de comandos pasados a la aplicación.  
  
 `pnRetCode`  
 HRESULT correspondiente al registro (si se llevó a cabo).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la aplicación debe continuar ejecutándose, de lo contrario, false.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama desde [CAtlExeModuleT::WinMain](#winmain) y se puede reemplazar para controlar los modificadores de línea de comandos. La implementación predeterminada busca **/regserver** y **/UnRegServer** argumentos de línea de comandos y realiza el registro o la anulación del registro.  
  
##  <a name="a-namepostmessageloopa--catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop  
 Este método se llama inmediatamente después de que se sale del bucle de mensaje.  
  
```
HRESULT PostMessageLoop() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para realizar la limpieza de la aplicación personalizada. La implementación predeterminada llama [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).  
  
##  <a name="a-namepremessageloopa--catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop  
 Este método se llama inmediatamente antes de entrar en el bucle de mensajes.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nShowCmd`  
 El valor pasado como el `nShowCmd` parámetro WinMain.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para agregar código de inicialización personalizada de la aplicación. La implementación predeterminada registra los objetos de clase.  
  
##  <a name="a-nameregisterclassobjectsa--catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects  
 Registra el objeto de clase con OLE para que otras aplicaciones puedan conectarse a él.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dwClsContext*  
 Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER.  
  
 `dwFlags`  
 Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE.  
  
### <a name="return-value"></a>Valor devuelto  
 Éxito, S_FALSE si no hay ninguna clase para registrar o un error HRESULT en caso contrario, devuelve S_OK.  
  
##  <a name="a-namerevokeclassobjectsa--catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects  
 Quita el objeto de clase.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Éxito, S_FALSE si no hay ninguna clase para registrar o un error HRESULT en caso contrario, devuelve S_OK.  
  
##  <a name="a-nameruna--catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Run  
 Este método se ejecuta código en el módulo EXE para inicializar, ejecutar el bucle de mensajes y limpiar.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nShowCmd`  
 Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sección. El valor predeterminado es SW_HIDE.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede invalidarse. Sin embargo, en la práctica es mejor invalidar [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), o [CAtlExeModuleT::PostMessageLoop](#postmessageloop) en su lugar.  
  
##  <a name="a-namerunmessageloopa--catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop  
 Este método ejecuta el bucle de mensajes.  
  
```
void RunMessageLoop() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se puede invalidar para cambiar el comportamiento de bucle de mensajes.  
  
##  <a name="a-nameuninitializecoma--catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom  
 Anula COM.  
  
```
static void UninitializeCom() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método simplemente llama a [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715) y se llama desde el destructor. Invalide este método si se reemplaza [a CAtlExeModuleT:: InitializeCom](#initializecom).  
  
##  <a name="a-nameunlocka--catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Unlock  
 Reduce el recuento de bloqueos del módulo.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="a-namewinmaina--catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain  
 Este método implementa el código necesario para ejecutar un archivo EXE.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nShowCmd`  
 Especifica cómo se mostrará la ventana. Este parámetro puede ser uno de los valores descritos en la [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sección.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de retorno del archivo ejecutable.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede invalidarse. Si reemplazar [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), o [CAtlExeModuleT::RunMessageLoop](#runmessageloop) no ofrece suficiente flexibilidad, es posible reemplazar el `WinMain` funcione con este método.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ATLDuck](../../visual-cpp-samples.md)   
 [Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
 [Clase CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

