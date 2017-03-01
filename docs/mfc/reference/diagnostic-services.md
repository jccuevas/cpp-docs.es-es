---
title: "Servicios de diagnóstico | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosis, diagnostic services
- diagnostic macros, list of general MFC
- services, diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables
- diagnostics, diagnostic functions and variables
- diagnostics, list of general MFC
- diagnosis, diagnostic functions and variables
- diagnosis, list of general MFC
- general diagnostic macros in MFC
- diagnostic macros
- diagnostic services
- object diagnostic functions in MFC
- diagnostics, diagnostic services
- diagnostic functions and variables
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 86fe366a4d7863fb9339b7b5a9f880103876de33
ms.lasthandoff: 02/24/2017

---
# <a name="diagnostic-services"></a>Servicios de diagnóstico
La biblioteca MFC (Microsoft Foundation Class) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:  
  
-   Macros de diagnóstico generales  
  
-   Funciones y variables de diagnóstico general  
  
-   Funciones de diagnóstico de objetos  
  
 Estas macros y funciones están disponibles para todas las clases derivan de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todos excepto `DEBUG_NEW` y **compruebe** no hacen nada en la versión de lanzamiento.  
  
 En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:  
  
 [!code-cpp[NVC_MFCCObjectSample&#14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en el archivo de implementación, todas las llamadas a **nuevo** almacenará el nombre de archivo y número de línea donde realizó la asignación de memoria. La función [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) mostrará esta información adicional, lo que permite identificar pérdidas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para obtener información adicional sobre los resultados de diagnóstico.  
  
 Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para obtener más información, consulte [depurar rutinas](../../c-runtime-library/debug-routines.md) en la referencia de la biblioteca de tiempo de ejecución.  
  
### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnóstico generales de MFC  
  
|||  
|-|-|  
|[ASSERT](#assert)|Imprime un mensaje y, a continuación, se anula el programa si la expresión especificada se evalúa como **FALSE** en la versión de depuración de la biblioteca.|  
|[ASSERT_KINDOF](#assert_kindof)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|  
|[ASSERT_VALID](#assert_valid)|Comprueba la validez interna de un objeto mediante una llamada a su `AssertValid` función miembro; normalmente invalidada desde `CObject`.|  
|[DEBUG_NEW](#debug_new)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|  
|[DEBUG_ONLY](#debug_only)|Similar a **ASSERT** pero no prueba el valor de la expresión; útil para el código que se debe ejecutar solo en modo de depuración.|  
|[TRACE](#trace)|Proporciona `printf`-como la capacidad de la versión de depuración de la biblioteca.|  
|[COMPROBAR](#verify)|Similar a **ASSERT** pero evalúa la expresión en la versión de la biblioteca, así como en la versión de depuración.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funciones y variables de diagnóstico general de MFC  
  
|||  
|-|-|  
|[afxDump](#afxdump)|Variable global que envía [CDumpContext](../../mfc/reference/cdumpcontext-class.md) información en la ventana de salida del depurador o en el terminal de depuración.|  
|[afxMemDF](#afxmemdf)|Variable global que controla el comportamiento del asignador de memoria de depuración.|  
|[AfxCheckError](#afxcheckerror)|Variable global que se usa para probar el pasado **SCODE** para ver si es un error y, si es así, se produce el error correspondiente.|  
|[AfxCheckMemory](#afxcheckmemory)|Comprueba la integridad de toda la memoria asignada actualmente.|  
|[AfxDump](#cdumpcontext_in_mfc_)|Si se llama mientras se encuentra en el depurador, vuelca el estado de un objeto durante la depuración.|  
|[AfxDumpStack](#afxdumpstack)|Genera una imagen de la pila actual. Esta función siempre está vinculada estáticamente.|  
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Habilita el volcado de fuga de memoria.|  
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Activa y desactiva el seguimiento de la memoria.|  
|[AfxIsMemoryBlock](#afxismemoryblock)|Comprueba que se ha asignado correctamente un bloque de memoria.|  
|[AfxIsValidAddress](#afxisvalidaddress)|Comprueba que un intervalo de direcciones de memoria se encuentra dentro de los límites del programa.|  
|[AfxIsValidString](#afxisvalidstring)|Determina si un puntero a una cadena es válido.|  
|[AfxSetAllocHook](#afxsetallochook)|Permite la llamada de una función en cada asignación de memoria.|  
  
### <a name="mfc-object-diagnostic-functions"></a>Funciones de diagnóstico de objetos de MFC  
  
|||  
|-|-|  
|[AfxDoForAllClasses](#afxdoforallclasses)|Realiza una función especificada en todos los `CObject`-clases derivadas que admiten la comprobación de tipos en tiempo de ejecución.|  
|[AfxDoForAllObjects](#afxdoforallobjects)|Realiza una función especificada en todos los `CObject`-objetos asignados con derivados **nueva**.|  
  
##  <a name="a-nameasserta--assert"></a><a name="assert"></a>ASSERT
 Se evalúa como su argumento.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y anula el programa. Si la condición es distinto de cero, no hace nada.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen, y *num* es el número de línea de la aserción con errores en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, **ASSERT** no se evalúa la expresión y, por tanto, no se interrumpirá el programa. Si la expresión se debe evaluar independientemente del entorno, use la **compruebe** (macro) en lugar de **ASSERT**.  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#44;](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameassertkindofa--assertkindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF  
 Esta macro se afirma que el objeto al que señala es un objeto de la clase especificada o es un objeto de una clase que deriva de la clase especificada.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parámetros  
 *nombre de clase*  
 El nombre de un `CObject`-clase derivada.  
  
 *pObject*  
 Puntero a un objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 El *pobject* parámetro debe ser un puntero a un objeto y puede ser **const**. El objeto al que apunta y debe ser compatible con la clase `CObject` información de clases en tiempo de ejecución. Por ejemplo, para asegurarse de que `pDocument` es un puntero a un objeto de la `CMyDoc` clase o cualquiera de sus derivados, código:  
  
 [!code-cpp[NVC_MFCDocView&#194;](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Mediante el `ASSERT_KINDOF` macro es exactamente igual que la codificación:  
  
 [!code-cpp[NVC_MFCDocView&#195;](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Esta función sólo funciona para las clases que se declara con el [DECLARE_DYNAMIC] (ejecución tiempo objeto modelo services.md #declare_dynamic o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) (macro).  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameassertvalida--assertvalid"></a><a name="assert_valid"></a>ASSERT_VALID  
 Usar para probar sus suposiciones acerca de la validez del estado interno de un objeto.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parámetros  
 `pObject`  
 Especifica un objeto de una clase derivada de `CObject` que tiene una versión de reemplazo de la `AssertValid` función miembro.  
  
### <a name="remarks"></a>Comentarios  
 `ASSERT_VALID`llamadas del `AssertValid` función de miembro del objeto pasado como argumento.  
  
 En la versión de lanzamiento de MFC, `ASSERT_VALID` no hace nada. En la versión de depuración, valida el puntero, se comprueba contra **NULL**y llama a la propia `AssertValid` funciones miembro. Si cualquiera de estas pruebas se produce un error, se muestra un mensaje de alerta de la misma manera que [ASSERT](#assert).  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  
  
 Para obtener más información y ejemplos, vea [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample Nº&19;](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-namedebugnewa--debugnew"></a><a name="debug_new"></a>DEBUG_NEW  
 Ayuda a buscar pérdidas de memoria.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `DEBUG_NEW` en todas partes en el programa que normalmente usaría el **nuevo** operador para asignar el almacenamiento de montón.  
  
 En modo de depuración (cuando el **_DEBUG** símbolo está definido), `DEBUG_NEW` realiza un seguimiento de lo nombre de archivo y número de línea para cada objeto que asigna. A continuación, cuando se usa el [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) función miembro, cada objeto asignado con `DEBUG_NEW` se muestra con el nombre de archivo y número de línea donde fue asignado.  
  
 Usar `DEBUG_NEW`, inserte la siguiente directiva en los archivos de origen:  
  
 [!code-cpp[NVC_MFCCObjectSample&#14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Una vez que inserte esta directiva, el preprocesador insertará `DEBUG_NEW` siempre que use **nueva**, y MFC encarga del resto. Cuando se compila una versión de lanzamiento del programa, `DEBUG_NEW` se resuelve como una simple **nuevo** operación y la información de número de nombre de archivo y línea no se generan.  
  
> [!NOTE]
>  En versiones anteriores de MFC (4.1 y anterior) necesarios para poner el `#define` instrucción después de todas las instrucciones que llama el `IMPLEMENT_DYNCREATE` o `IMPLEMENT_SERIAL` las macros. Esto ya no es necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-namedebugonlya--debugonly"></a><a name="debug_only"></a>DEBUG_ONLY  
 En modo de depuración (cuando el **_DEBUG** símbolo está definido), `DEBUG_ONLY` se evalúa como su argumento.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Comentarios  
 En una versión de lanzamiento, **DEBUG_ONLY** no evalúa su argumento. Esto es útil cuando dispone de código que se debe ejecutar solo en compilaciones de depuración.  
  
 El `DEBUG_ONLY` macro es equivalente a la que rodean *expresión* con **#ifdef _DEBUG** y `#endif`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#32;](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-nametracea--trace"></a><a name="trace"></a>SEGUIMIENTO  
 Envía la cadena especificada al depurador de la aplicación actual.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [ATLTRACE2](http://msdn.microsoft.com/library/467ff555-e7a5-4f94-bdd9-50ee27ab9986) para obtener una descripción de **seguimiento**. **SEGUIMIENTO** y `ATLTRACE2` tienen el mismo comportamiento.  
  
 En la versión de depuración de MFC, esta macro envía la cadena especificada al depurador de la aplicación actual. En una versión de lanzamiento, esta macro se compila en nothing (código no se genera en absoluto).  
  
 Para obtener más información, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-nameverifya--verify"></a><a name="verify"></a>COMPROBAR  
 En la versión de depuración de MFC, se evalúa como su argumento.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y detiene el programa. Si la condición es distinto de cero, no hace nada.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen y *num* es el número de línea de la aserción con errores en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, **compruebe** evalúa la expresión pero no imprimir ni interrumpir el programa. Por ejemplo, si la expresión es una llamada de función, se realiza la llamada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#198;](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-namecdumpcontextinmfca--afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc_"></a>afxDump (CDumpContext en MFC)  
 Proporciona la capacidad básica de volcado de objetos en la aplicación.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Comentarios  
 `afxDump`está predefinido [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto que le permite enviar `CDumpContext` información en la ventana de salida del depurador o en un terminal de depuración. Normalmente, proporcionar `afxDump` como un parámetro para `CObject::Dump`.  
  
 En Windows NT y todas las versiones de Windows, `afxDump` salida se envía a la ventana de salida de depuración de Visual C++, cuando se depura la aplicación.  
  
 Esta variable se define en la versión de depuración de MFC. Para obtener más información sobre `afxDump`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFC_Utilities #](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-nameafxmemdfa--afxmemdf"></a><a name="afxmemdf"></a>afxMemDF  
 Esta variable es accesible desde un depurador o el programa y permite ajustar el diagnóstico de la asignación.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Comentarios  
 `afxMemDF`puede tener los siguientes valores según lo especificado por la enumeración `afxMemDF`:  
  
- **allocMemDF** activa el asignador de depuración (valor predeterminado en la biblioteca de depuración).  
  
- **delayFreeMemDF** retrasa la liberación de memoria. Mientras el programa libera un bloque de memoria, el asignador no devuelve esa memoria para el sistema operativo subyacente. Esto colocará la carga máxima de memoria en el programa.  
  
- **checkAlwaysMemDF** llamadas `AfxCheckMemory` cada vez que se asigna o se libera memoria. Esto ralentiza considerablemente las cancelaciones de asignación y asignaciones de memoria.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities Nº&30;](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-nameafxcheckerrora--afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError  
 Esta función comprueba el pasado **SCODE** para ver si es un error.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error, la función produce una excepción. Si el pasado `SCODE` es **E_OUTOFMEMORY**, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) llamando a [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). De lo contrario, la función produce una [COleException](../../mfc/reference/coleexception-class.md) llamando a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Esta función puede utilizarse para comprobar los valores devueltos de las llamadas a funciones OLE en la aplicación. Probar el valor devuelto por esta función en la aplicación, puede reaccionar correctamente a las condiciones de error con una cantidad mínima de código.  
  
> [!NOTE]
>  Esta función tiene el mismo efecto en modo de depuración y no de depuración.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&33;](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="a-nameafxcheckmemorya--afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory  
 Esta función valida el bloque de memoria libre e imprime los mensajes de error según sea necesario.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si no hay errores de memoria; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si la función detecta que no hay daños en la memoria, se imprime nada.  
  
 Se comprueban todos los bloques de memoria asignados actualmente en el montón, incluidos aquellos asignados por **nueva** pero no los que se asignan mediante llamadas directas a los asignadores de memoria subyacente, como el `malloc` función o la **GlobalAlloc** función de Windows. Si se encuentra cualquier bloque dañado, se imprime un mensaje a la salida del depurador.  
  
 Si incluye la línea  
  
 [!code-cpp[NVC_MFCCObjectSample&#14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en un módulo de programa, las llamadas posteriores a `AfxCheckMemory` mostrar el nombre de archivo y número de línea donde se asignó la memoria.  
  
> [!NOTE]
>  Si el módulo contiene una o varias implementaciones de las clases serializables, debe colocar la `#define` línea después de la última `IMPLEMENT_SERIAL` llamada de macro.  
  
 Esta función sólo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCCObjectSample #](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
 
##  <a name="a-namemfca--afxdump-mfc"></a><a name="mfc_"></a>AfxDump (MFC)  
 Llame a esta función en el depurador para volcar el estado de un objeto durante la depuración.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pOb`  
 Un puntero a un objeto de una clase derivada de `CObject`.  
  
### <a name="remarks"></a>Comentarios  
 **AfxDump** llama a un objeto `Dump` función miembro y envía la información a la ubicación especificada por el `afxDump` variable. **AfxDump** sólo está disponible en la versión de depuración de MFC.  
  
 El código del programa no debe llamar a **AfxDump**, pero en su lugar, debe llamar a la `Dump` función de miembro del objeto correspondiente.  
  
##  <a name="a-nameafxdumpstacka--afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack  
 Esta función global puede utilizarse para generar una imagen de la pila actual.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTarget*  
 Indica el destino de la salida de volcado de memoria. Los valores posibles que se pueden combinar mediante la operación bit a bit OR ( **|**) (operador), son los siguientes:  
  
- **AFX_STACK_DUMP_TARGET_TRACE** envía los resultados por medio de la [seguimiento](#trace) macro. El **seguimiento** macro genera salida en las compilaciones de depuración; en versiones de lanzamiento no genera ningún resultado. Además, **seguimiento** pueden redirigirse a otros destinos además el depurador.  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT** envía vuelque el resultado en el destino predeterminado. Para una compilación de depuración, la salida se dirige a la **seguimiento** macro. En una versión de lanzamiento, salida va al Portapapeles.  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD** envía los resultados al Portapapeles únicamente. Los datos se colocan en el Portapapeles como texto sin formato mediante el **CF_TEXT** formato del Portapapeles.  
  
- **AFX_STACK_DUMP_TARGET_BOTH** envía los resultados en el Portapapeles y la **seguimiento** (macro), al mismo tiempo.  
  
- **AFX_STACK_DUMP_TARGET_ODS** envía los resultados directamente en el depurador mediante la función de Win32 **OutputDebugString()**. Esta opción generará el resultado de la depuración en ambas versiones de depuración y lanzamiento cuando se adjunta un depurador al proceso. **AFX_STACK_DUMP_TARGET_ODS** siempre alcanza el depurador (si está conectado) y no se pueden redirigir.  
  
### <a name="remarks"></a>Comentarios  
 El siguiente ejemplo refleja una sola línea de la salida generada de llamar al método `AfxDumpStack` de un controlador del botón en una aplicación de cuadro de diálogo MFC:  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 Cada línea en la salida anterior indica la dirección de la última llamada de función, el nombre de ruta de acceso completa del módulo que contiene la llamada de función y el prototipo de función que llama. Si la llamada de función en la pila no se realiza en la dirección exacta de la función, se muestra un desplazamiento de bytes.  
  
 Por ejemplo, en la tabla siguiente se describe la primera línea de la salida anterior:  
  
|Salida|Descripción|  
|------------|-----------------|  
|`00427D55:`|La dirección de retorno de la última llamada de función.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|El nombre de ruta de acceso completa del módulo que contiene la llamada de función.|  
|`void AfxDumpStack(unsigned long)`|El prototipo de función se llama.|  
|`+ 181 bytes`|Desplazamiento en bytes de la dirección del prototipo de función (en este caso, `void AfxDumpStack(unsigned long)`) a la dirección de retorno (en este caso, `00427D55`).|  
  
 `AfxDumpStack`está disponible en versiones de depuración y nondebug de las bibliotecas MFC; Sin embargo, la función siempre está vinculada estáticamente, incluso cuando el archivo ejecutable utiliza MFC en un archivo DLL compartido. En las implementaciones de la biblioteca compartida, la función se encuentra en la MFCS42. Biblioteca LIB (y sus variantes).  
  
 Para utilizar correctamente esta función:  
  
-   El archivo IMAGEHLP. DLL debe estar en la ruta de acceso. Si no tiene este archivo DLL, la función mostrará un mensaje de error. Consulte [imagen de la biblioteca de Ayuda](http://msdn.microsoft.com/library/windows/desktop/ms680321) para obtener información sobre el conjunto de funciones proporcionado por IMAGEHLP.  
  
-   Los módulos que tienen marcos en la pila deben incluir información de depuración. Si no contienen información de depuración, la función generará un seguimiento de pila, pero el seguimiento será menos detallado.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxenablememoryleakdumpa--afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump  
 Habilita y deshabilita el volcado de pérdida de memoria en el destructor `AFX_DEBUG_STATE` .  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDump`  
 `TRUE` indica que el volcado de pérdida de memoria está habilitado, mientras que `FALSE` indica que está deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor anterior de esta marca.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación descarga la biblioteca MFC, esta comprueba si hay pérdidas de memoria. En este punto, las pérdidas de memoria se notifican al usuario a través de la **depurar** ventana de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Si la aplicación carga otra biblioteca antes que la biblioteca MFC, algunas asignaciones de memoria de la biblioteca se notificarán incorrectamente como pérdidas de memoria. Las pérdidas de memoria falsas pueden hacer que la aplicación se cierre lentamente, ya que la biblioteca MFC las estará notificando. En este caso, use `AfxEnableMemoryLeakDump` para deshabilitar el volcado de pérdida de memoria.  
  
> [!NOTE]
>  Si usa este método para desactivar el volcado de pérdida de memoria, no recibirá ningún informe de pérdidas de memoria válidas en la aplicación. Solo debe usar este método si está seguro de que el informe de pérdida de memoria contiene pérdidas de memoria falsas.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxenablememorytrackinga--afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking  
 Memoria para diagnósticos de seguimiento se activa normalmente en la versión de depuración de MFC.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parámetros  
 *bTrack*  
 Establecer este valor en **TRUE** activa el seguimiento; de la memoria **FALSE** lo desactiva.  
  
### <a name="return-value"></a>Valor devuelto  
 La configuración anterior de la marca de habilitar el seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para deshabilitar el seguimiento de las secciones del código que sabe que son los bloques se asignan correctamente.  
  
 Para obtener más información sobre `AfxEnableMemoryTracking`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Esta función sólo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#24;](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxismemoryblocka--afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock  
 Una dirección de memoria para asegurarse de que representa un bloque de memoria activas actualmente asignada por la versión de diagnóstico de las pruebas **nueva**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Señala al bloque de memoria se va a probar.  
  
 `nBytes`  
 Contiene la longitud del bloque de memoria en bytes.  
  
 `plRequestNumber`  
 Apunta a un **largo** entero que se rellenará con el número de secuencia de asignación del bloque de memoria, o cero si no representa un bloque de memoria activas actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el bloque de memoria está actualmente asignado y la longitud es correcta. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 También comprueba el tamaño especificado en el tamaño asignado original. Si la función devuelve cero, se devuelve el número de secuencia de asignación en `plRequestNumber`. Este número representa el orden en que se asignó el bloque en relación con todos los demás **nuevo** asignaciones.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities Nº&27;](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxisvalidaddressa--afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress  
 Pruebas de cualquier dirección de memoria para asegurarse de que está contenido totalmente en el espacio de memoria del programa.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lp`  
 Apunta a la dirección de memoria que se va a probar.  
  
 `nBytes`  
 Contiene el número de bytes de memoria que se va a probar.  
  
 *bReadWrite*  
 Especifica si la memoria es de lectura y escritura ( **TRUE**) o solo lectura ( **FALSE**).  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, distinto de cero si bloquea la memoria especificada está dentro de completamente espacio de memoria del programa; en caso contrario, 0.  
  
 En versiones no depuradas, cero si `lp` no es NULL; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La dirección no está restringida a bloques asignados por **nueva**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#28;](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxisvalidstringa--afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString  
 Utilice esta función para determinar si es válido un puntero a una cadena.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Puntero que se va a probar.  
  
 `nLength`  
 Especifica la longitud de la cadena que se va a probar, en bytes. Un valor de â €"1 indica que será la cadena terminada en null.  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, distinto de cero si el puntero especificado que apunta a una cadena del tamaño especificado; en caso contrario, 0.  
  
 En versiones no depuradas, cero si `lpsz` no es NULL; de lo contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#29;](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxsetallochooka--afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook  
 Establece un enlace que permite realizar la llamada de la función especificada antes de que se asigna cada bloque de memoria.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parámetros  
 *pfnAllocHook*  
 Especifica el nombre de la función de llamada. Vea la sección Comentarios para el prototipo de una función de asignación.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si desea permitir la asignación; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El asignador de memoria de depuración de Microsoft Foundation Class Library puede llamar a una función de enlace definidos por el usuario para permitir que el usuario para supervisar una asignación de memoria y controlar si se permite la asignación. Funciones de enlace de asignación son un prototipo:  
  
 **BOOL AFXAPI AllocHook( size_t** `nSize`**, BOOL** `bObject`**, LONG** `lRequestNumber` **);**  
  
 `nSize`  
 El tamaño de la asignación de memoria propuesto.  
  
 `bObject`  
 **TRUE** si la asignación es para un `CObject`-objeto derivado; en caso contrario **FALSE**.  
  
 `lRequestNumber`  
 Número de secuencia de la asignación de memoria.  
  
 Tenga en cuenta que el **AFXAPI** convención de llamada implica que el destinatario debe quitar los parámetros de la pila.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxdoforallclassesa--afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses  
 Llama a la función de la iteración especificada para serializar `CObject`-clases derivadas en el espacio de memoria de la aplicación.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pfn`  
 Señala a una función de iteración para llamarlo para cada clase. Los argumentos de función son un puntero a un `CRuntimeClass` objeto y un puntero void para los datos adicionales que proporciona el autor de la llamada a la función.  
  
 `pContext`  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Serializable `CObject`-clases derivadas son clases derivadas con el `DECLARE_SERIAL` (macro). El puntero que se pasa a `AfxDoForAllClasses` en `pContext` se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función sólo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#113;](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections&#114;](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameafxdoforallobjectsa--afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects  
 Ejecuta la función de la iteración especificada de todos los objetos derivados de `CObject` que se han asignado con **nueva**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pfn`  
 Señala a una función de iteración para ejecutar para cada objeto. Los argumentos de función son un puntero a un `CObject` y un puntero void para los datos adicionales que proporciona el autor de la llamada a la función.  
  
 `pContext`  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 No se enumeran pila, global, u objetos incrustados. El puntero pasado a `AfxDoForAllObjects` en `pContext` se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función sólo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#115;](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections&#116;](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
