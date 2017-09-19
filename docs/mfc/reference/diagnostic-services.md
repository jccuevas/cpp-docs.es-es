---
title: "Servicios de diagnóstico | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: ceaf02cbe0eedec6e8bd4980d87c025d6aa23615
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="diagnostic-services"></a>Servicios de diagnóstico
La biblioteca MFC (Microsoft Foundation Class) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:  
  
-   Macros de diagnóstico generales  
  
-   Funciones y variables de diagnóstico general  
  
-   Funciones de diagnóstico de objetos  
  
 Estas macros y funciones están disponibles para todas las clases derivan de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todos excepto `DEBUG_NEW` y **compruebe** no hacen nada en la versión de lanzamiento.  
  
 En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:  
  
 [!code-cpp[NVC_MFCCObjectSample #14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en el archivo de implementación, todas las llamadas a **nueva** almacenará el nombre de archivo y número de línea donde realizó la asignación de memoria. La función [CMemoryState:: DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) mostrará esta información adicional, lo que le permite identificar pérdidas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para obtener más información sobre los resultados de diagnóstico.  
  
 Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para obtener más información, consulte [rutinas de depuración](../../c-runtime-library/debug-routines.md) en la referencia de la biblioteca de tiempo de ejecución.  
  
### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnóstico generales de MFC  
  
|||  
|-|-|  
|[ASSERT](#assert)|Imprime un mensaje y, a continuación, se anula el programa si la expresión especificada se evalúa como **FALSE** en la versión de depuración de la biblioteca.|  
|[ASSERT_KINDOF](#assert_kindof)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|  
|[ASSERT_VALID](#assert_valid)|Comprueba la validez interna de un objeto mediante una llamada a su `AssertValid` función miembro; normalmente invalidada desde `CObject`.|
|[DEBUG_NEW](#debug_new)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|  
|[DEBUG_ONLY](#debug_only)|Similar a **ASSERT** pero no prueba el valor de la expresión; útil para el código que se debe ejecutar solo en modo de depuración.|  
|[Asegúrese de que y ENSURE_VALID](#ensure)|Usar para validar la corrección de datos.|
|[THIS_FILE](#this_file)|Se expande al nombre del archivo que se está compilando.|
|[TRACE](#trace)|Proporciona `printf`-como capacidad en la versión de depuración de la biblioteca.|  
|[COMPROBAR](#verify)|Similar a **ASSERT** pero evalúa la expresión en la versión de lanzamiento de la biblioteca, así como en la versión de depuración.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funciones y variables de diagnóstico general de MFC  
  
|||  
|-|-|  
|[afxDump](#afxdump)|Variable global que envía [CDumpContext](../../mfc/reference/cdumpcontext-class.md) información en la ventana de salida del depurador o al terminal de depuración.|  
|[afxMemDF](#afxmemdf)|Variable global que controla el comportamiento del asignador de memoria de depuración.|  
|[AfxCheckError](#afxcheckerror)|Variable global que se utiliza para probar el valor **SCODE** para ver si es un error y, si es así, genera el error correspondiente.|  
|[AfxCheckMemory](#afxcheckmemory)|Comprueba la integridad de toda la memoria asignada actualmente.|  
|[AfxDebugBreak](#afxdebugbreak)|Produce una interrupción en ejecución.|
|[AfxDump](#cdumpcontext_in_mfc)|Si se llama mientras se encuentra en el depurador, vuelca el estado de un objeto durante la depuración.|  
|[AfxDump](#afxdump)|Función interna que vuelca el estado de un objeto durante la depuración.|
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

### <a name="mfc-compilation-macros"></a>Macros de compilación de MFC
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Suprime las advertencias del compilador para el uso de funciones en desuso de MFC.|  


## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS
Suprime las advertencias del compilador para el uso de funciones en desuso de MFC.  
   
### <a name="syntax"></a>Sintaxis   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>Ejemplo  
 Este ejemplo de código podría causar una advertencia del compilador si no se definieron _AFX_SECURE_NO_WARNINGS.  
  
 ```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a>AfxDebugBreak
Llame a esta función para producir una interrupción (en la ubicación de la llamada a `AfxDebugBreak`) en la ejecución de la versión de depuración de la aplicación MFC.  

### <a name="syntax"></a>Sintaxis    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Comentarios  
 `AfxDebugBreak`no tiene ningún efecto en las versiones de lanzamiento de una aplicación MFC y se debería quitar. Esta función sólo debe utilizarse en aplicaciones MFC. Usar la versión de API de Win32, **DebugBreak**, para producir una interrupción en las aplicaciones no están basados en MFC.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxver_.h   

##  <a name="assert"></a>ASSERT
 Se evalúa como su argumento.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y anula el programa. Si la condición es distinto de cero, no realiza ninguna acción.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen, y *num* es el número de línea de la aserción que generaron errores en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, **ASSERT** no se evalúa la expresión y, por tanto, no se interrumpirá el programa. Si la expresión debe evaluarse independientemente del entorno, use el **compruebe** macro en lugar de **ASSERT**.  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="assert_kindof"></a>ASSERT_KINDOF  
 Esta macro se afirma que el objeto al que señala a un objeto de la clase especificada o es un objeto de una clase que deriva de la clase especificada.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parámetros  
 *nombre de clase*  
 El nombre de un `CObject`-clase derivada.  
  
 *pObject*  
 Un puntero a un objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 El *pobject* parámetro debe ser un puntero a un objeto y puede ser **const**. El objeto al que apunta y debe ser compatible con la clase `CObject` información de clase en tiempo de ejecución. Por ejemplo, para asegurarse de que `pDocument` es un puntero a un objeto de la `CMyDoc` clase o cualquiera de sus derivados, se podría codificar:  
  
 [!code-cpp[NVC_MFCDocView #194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Mediante el `ASSERT_KINDOF` macro es exactamente igual que la codificación:  
  
 [!code-cpp[NVC_MFCDocView #195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Esta función solo funciona para las clases que se declara con el [DECLARE_DYNAMIC] (ejecución tiempo objeto modelo services.md #declare_dynamic o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="assert_valid"></a>ASSERT_VALID  
 Usar para probar sus suposiciones acerca de la validez del estado interno de un objeto.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parámetros  
 `pObject`  
 Especifica un objeto de una clase derivada de `CObject` que tiene una versión de reemplazo de la `AssertValid` función miembro.  
  
### <a name="remarks"></a>Comentarios  
 `ASSERT_VALID`llamadas a la `AssertValid` función de miembro del objeto pasado como argumento.  
  
 En la versión de lanzamiento de MFC, `ASSERT_VALID` no hace nada. En la versión de depuración, valida el puntero, se realiza una comprobación contra **NULL**y llama a la propia `AssertValid` funciones miembro. Si cualquiera de estas pruebas se produce un error, se muestra un mensaje de alerta en la misma manera que [ASSERT](#assert).  
  
> [!NOTE]
>  Esta función está disponible sólo en la versión de depuración de MFC.  
  
 Para obtener más información y ejemplos, vea [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample #19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="debug_new"></a>DEBUG_NEW  
 Ayuda a buscar pérdidas de memoria.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `DEBUG_NEW` en cualquier lugar en el programa que le gustaría usar normalmente el **nueva** operador que se va a asignar el almacenamiento de montón.  
  
 En modo de depuración (cuando la **_DEBUG** símbolo está definido), `DEBUG_NEW` realiza un seguimiento de lo nombre de archivo y número de línea para cada objeto que asigna. A continuación, cuando se usa el [CMemoryState:: DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) función miembro, cada objeto asignado con `DEBUG_NEW` se muestra con el nombre de archivo y número de línea donde fue asignado.  
  
 Para usar `DEBUG_NEW`, inserte la siguiente directiva en los archivos de origen:  
  
 [!code-cpp[NVC_MFCCObjectSample #14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Una vez insertada esta directiva, el preprocesador insertará `DEBUG_NEW` , donde use **nueva**, y MFC encarga del resto. Cuando se compila una versión de lanzamiento del programa, `DEBUG_NEW` se resuelve como una simple **nueva** operación y la información de número de nombre de archivo y la línea no se generan.  
  
> [!NOTE]
>  En versiones anteriores de MFC (4.1 y anterior) necesaria para colocar el `#define` instrucción después de todas las instrucciones que llama el `IMPLEMENT_DYNCREATE` o `IMPLEMENT_SERIAL` macros. Esto ya no es necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="debug_only"></a>DEBUG_ONLY  
 En modo de depuración (cuando la **_DEBUG** símbolo está definido), `DEBUG_ONLY` evalúa su argumento.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Comentarios  
 En una versión de lanzamiento, **DEBUG_ONLY** no evalúa su argumento. Esto es útil si tiene código que se debe ejecutar únicamente en las compilaciones de depuración.  
  
 El `DEBUG_ONLY` macro equivale a que rodean *expresión* con **#ifdef _DEBUG** y `#endif`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

 ### <a name="ensure"></a>Asegúrese de que y ENSURE_VALID
Usar para validar la corrección de datos.  
   
### <a name="syntax"></a>Sintaxis    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión booleana que se va a probar.  
   
### <a name="remarks"></a>Comentarios  
 El propósito de estas macros es mejorar la validación de parámetros. Las macros impiden continuar el proceso de parámetros incorrectos en el código. A diferencia de la **ASSERT** macros, el **Asegúrese** macros producen una excepción además de generar una aserción.  
  
 Las macros se comporten de dos maneras, según la configuración del proyecto. La llamada de macros **ASSERT** y, a continuación, inicia una excepción si se produce un error en la aserción. Por lo tanto, en configuraciones de depuración (es decir, donde **_DEBUG** está definido) las macros de producen una aserción y la excepción mientras se encuentra en las configuraciones de versión, las macros producen solo la excepción (**ASSERT** no se evalúa la expresión en configuraciones de versión).  
  
 La macro **ENSURE_ARG** actúa como el **Asegúrese** macro.  
  
 **ENSURE_VALID** llamadas el `ASSERT_VALID` macro (que tiene un efecto únicamente en las compilaciones de depuración). Además, **ENSURE_VALID** produce una excepción si el puntero es NULL. Se realiza la prueba NULL en configuraciones Debug y Release.  
  
 Si cualquiera de estas pruebas se produce un error, se muestra un mensaje de alerta en la misma manera que **ASSERT**. La macro produce una excepción de argumento no válido si es necesario.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [COMPROBAR](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a>THIS_FILE
Se expande al nombre del archivo que se está compilando.  
   
### <a name="syntax"></a>Sintaxis    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Comentarios  
 La información se usa por la **ASSERT** y **compruebe** macros. Los asistentes de Asistente para aplicaciones y código de colocar la macro en los archivos de código fuente que creen.  
   
### <a name="example"></a>Ejemplo  
```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the 
// compiler recognizes. 
```
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [ASSERT](#assert)   
 [COMPROBAR](#verify)


##  <a name="trace"></a>SEGUIMIENTO  
 Envía la cadena especificada al depurador de la aplicación actual.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) para obtener una descripción de **seguimiento**. **SEGUIMIENTO** y `ATLTRACE2` tienen el mismo comportamiento.  
  
 En la versión de depuración de MFC, esta macro envía la cadena especificada al depurador de la aplicación actual. En una versión de lanzamiento, esta macro se compila a nada (código no se genera en absoluto).  
  
 Para obtener más información, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="verify"></a>COMPROBAR  
 En la versión de depuración de MFC, se evalúa como su argumento.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y detiene el programa. Si la condición es distinto de cero, no realiza ninguna acción.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen y *num* es el número de línea de la aserción que generaron errores en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, **compruebe** evalúa la expresión pero no imprimir ni interrumpir el programa. Por ejemplo, si la expresión es una llamada de función, se realizará la llamada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext en MFC)  
 Proporciona funcionalidad básica volcado de objetos en la aplicación.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Comentarios  
 `afxDump`está predefinido [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto que le permite enviar `CDumpContext` información en la ventana de salida del depurador o en un terminal de depuración. Por lo general, proporcionar `afxDump` como un parámetro a `CObject::Dump`.  
  
 En Windows NT y todas las versiones de Windows, `afxDump` la salida se envía a la ventana de salida de depuración de Visual C++ cuando se depura la aplicación.  
  
 Esta variable solo se define en la versión de depuración de MFC. Para obtener más información sobre `afxDump`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h


## <a name="afxdump"></a>AfxDump (interno)
Función interna que utiliza MFC para volcar el estado de un objeto durante la depuración.  

### <a name="syntax"></a>Sintaxis    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Parámetros  
 `pOb`  
 Un puntero a un objeto de una clase derivada de `CObject`.  
   
### <a name="remarks"></a>Comentarios  
 **AfxDump** llama a un objeto `Dump` función miembro y envía la información a la ubicación especificada por el `afxDump` variable. **AfxDump** solo está disponible en la versión de depuración de MFC.  
  
 El código del programa no debe llamar a **AfxDump**, pero en su lugar, debe llamar a la `Dump` función de miembro del objeto correspondiente.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>afxMemDF  
 Esta variable es accesible desde un depurador o el programa y le permite optimizar el diagnóstico de asignación.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Comentarios  
 `afxMemDF`puede tener los valores siguientes según lo especificado por la enumeración `afxMemDF`:  
  
- **allocMemDF** activa el asignador de depuración (valor predeterminado en la biblioteca de depuración).  
  
- **delayFreeMemDF** retrasa la liberación de memoria. Mientras el programa libera un bloque de memoria, el asignador no devuelve esa memoria para el sistema operativo subyacente. Esto provocará el esfuerzo de la cantidad máxima de memoria en el programa.  
  
- **checkAlwaysMemDF** llamadas `AfxCheckMemory` cada vez que se asigna o se libera memoria. Esto ralentiza notablemente cancelaciones de asignación y asignaciones de memoria.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="afxcheckerror"></a>AfxCheckError  
 Esta función comprueba el valor **SCODE** para ver si se trata de un error.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error, la función produce una excepción. Si el valor `SCODE` es **E_OUTOFMEMORY**, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) mediante una llamada a [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). En caso contrario, la función produce una [COleException](../../mfc/reference/coleexception-class.md) mediante una llamada a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Esta función puede utilizarse para comprobar los valores devueltos de las llamadas a funciones OLE en la aplicación. Al probar el valor devuelto con esta función en la aplicación, pueden reaccionar correctamente ante situaciones de error con una cantidad mínima de código.  
  
> [!NOTE]
>  Esta función tiene el mismo efecto en versiones de depuración y las compilaciones de depuración no.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº 33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="afxcheckmemory"></a>AfxCheckMemory  
 Esta función valida el bloque de memoria libre e imprime los mensajes de error según sea necesario.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no hay errores de memoria; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si la función detecta que no hay daños en la memoria, se imprime nada.  
  
 Se comprueban todos los bloques de memoria asignados actualmente en el montón, las asignadas por incluidas **nueva** pero no las asignada por llamadas directas a los asignadores de memoria subyacente, como el `malloc` función o la **GlobalAlloc** la función de Windows. Si se encuentra cualquier bloque que está dañado, se imprime un mensaje en la salida del depurador.  
  
 Si incluye la línea  
  
 [!code-cpp[NVC_MFCCObjectSample #14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en un módulo de programa, las llamadas posteriores, a continuación, al `AfxCheckMemory` mostrar el nombre de archivo y número de línea donde se asignó la memoria.  
  
> [!NOTE]
>  Si el módulo contiene una o varias implementaciones de las clases serializables, debe colocar la `#define` línea después de la última `IMPLEMENT_SERIAL` llamada de macro.  
  
 Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de # NVC_MFCCObjectSample](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
 
##  <a name="afxdump"></a>AfxDump (MFC)  
 Llame a esta función en el depurador para volcar el estado de un objeto durante la depuración.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pOb`  
 Un puntero a un objeto de una clase derivada de `CObject`.  
  
### <a name="remarks"></a>Comentarios  
 **AfxDump** llama a un objeto `Dump` función miembro y envía la información a la ubicación especificada por el `afxDump` variable. **AfxDump** solo está disponible en la versión de depuración de MFC.  
  
 El código del programa no debe llamar a **AfxDump**, pero en su lugar, debe llamar a la `Dump` función de miembro del objeto correspondiente.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  

### <a name="see-also"></a>Vea también  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>AfxDumpStack  
 Esta función global puede utilizarse para generar una imagen de la pila actual.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTarget*  
 Indica el destino de la salida de volcado de memoria. Posibles valores, que se pueden combinar con la operación bit a bit OR ( **|**) (operador), son los siguientes:  
  
- **AFX_STACK_DUMP_TARGET_TRACE** envía los resultados por medio de la [seguimiento](#trace) macro. El **seguimiento** macro genera salida en las compilaciones de depuración solo; no se genera ningún resultado en versiones de lanzamiento. Además, **seguimiento** puede redirigirse a otros destinos además el depurador.  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT** envía vuelque el resultado en el destino predeterminado. Para una compilación de depuración, la salida se dirige a la **seguimiento** macro. En una versión de lanzamiento, resultado se pasa en el Portapapeles.  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD** envía los resultados en el Portapapeles únicamente. Los datos se colocan en el Portapapeles como texto sin formato mediante la **CF_TEXT** formato del Portapapeles.  
  
- **AFX_STACK_DUMP_TARGET_BOTH** envía los resultados en el Portapapeles y a la **seguimiento** macro, al mismo tiempo.  
  
- **AFX_STACK_DUMP_TARGET_ODS** envía los resultados directamente al depurador por medio de la función de Win32 **OutputDebugString()**. Esta opción generará el resultado de la depuración en ambas versiones de depuración y lanzamiento cuando se adjunta un depurador al proceso. **AFX_STACK_DUMP_TARGET_ODS** siempre alcanza el depurador (si está conectado) y no se pueden redirigir.  
  
### <a name="remarks"></a>Comentarios  
 En el ejemplo siguiente refleja una sola línea de la salida generada de llamar al método `AfxDumpStack` de un controlador de botón en una aplicación de cuadro de diálogo MFC:  
  
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
  
 Por ejemplo, en la tabla siguiente se describen la primera línea de la salida anterior:  
  
|Salida|Descripción|  
|------------|-----------------|  
|`00427D55:`|La dirección de devolución de la última llamada de función.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|El nombre de ruta de acceso completa del módulo que contiene la llamada de función.|  
|`void AfxDumpStack(unsigned long)`|El prototipo de función se llama.|  
|`+ 181 bytes`|Desplazamiento en bytes de la dirección del prototipo de función (en este caso, `void AfxDumpStack(unsigned long)`) a la dirección de retorno (en este caso, `00427D55`).|  
  
 `AfxDumpStack`está disponible en versiones de depuración y nondebug de las bibliotecas MFC; Sin embargo, la función siempre está vinculada estáticamente, incluso cuando el archivo ejecutable utiliza MFC en un archivo DLL compartido. En implementaciones de biblioteca compartida, la función se encuentra en la MFCS42. Biblioteca LIB (y sus variantes).  
  
 Para usar esta función correctamente:  
  
-   El archivo IMAGEHLP. Archivo DLL debe estar en la ruta de acceso. Si no tiene este archivo DLL, la función mostrará un mensaje de error. Vea [bibliotecas de Ayuda de imagen](http://msdn.microsoft.com/library/windows/desktop/ms680321) para obtener información sobre el conjunto de funciones proporcionado por IMAGEHLP.  
  
-   Los módulos que tienen marcos en la pila deben incluir información de depuración. Si no contienen información de depuración, la función seguirá generando un seguimiento de pila, pero el seguimiento será menos detallado.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump  
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
 Cuando una aplicación descarga la biblioteca MFC, esta comprueba si hay pérdidas de memoria. En este momento, las pérdidas de memoria se notifican al usuario a través de la **depurar** ventana de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Si la aplicación carga otra biblioteca antes que la biblioteca MFC, algunas asignaciones de memoria de la biblioteca se notificarán incorrectamente como pérdidas de memoria. Las pérdidas de memoria falsas pueden hacer que la aplicación se cierre lentamente, ya que la biblioteca MFC las estará notificando. En este caso, use `AfxEnableMemoryLeakDump` para deshabilitar el volcado de pérdida de memoria.  
  
> [!NOTE]
>  Si usa este método para desactivar el volcado de pérdida de memoria, no recibirá ningún informe de pérdidas de memoria válidas en la aplicación. Solo debe usar este método si está seguro de que el informe de pérdida de memoria contiene pérdidas de memoria falsas.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxenablememorytracking"></a>AfxEnableMemoryTracking  
 Memoria para diagnósticos de seguimiento se activa normalmente en la versión de depuración de MFC.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parámetros  
 *bTrack*  
 Establecer este valor en **TRUE** activa el seguimiento; de la memoria **FALSE** apaga el equipo.  
  
### <a name="return-value"></a>Valor devuelto  
 La configuración anterior de la marca de seguimiento a habilitar.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para deshabilitar el seguimiento en las secciones del código que sabe que son los bloques se asignan correctamente.  
  
 Para obtener más información sobre `AfxEnableMemoryTracking`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxismemoryblock"></a>AfxIsMemoryBlock  
 Comprueba una dirección de memoria para asegurarse de que representa un bloque de memoria activas actualmente que se asignó mediante la versión de diagnóstico de **nueva**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Apunta a un bloque de memoria se va a probar.  
  
 `nBytes`  
 Contiene la longitud del bloque de memoria en bytes.  
  
 `plRequestNumber`  
 Apunta a un **largo** entero que se rellenará con el número de secuencia de asignación del bloque de memoria, o cero si no representa un bloque de memoria activas actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el bloque de memoria está asignado actualmente y la longitud es correcta; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 También comprueba el tamaño especificado en el tamaño de la asignación original. Si la función devuelve un valor distinto de cero, se devuelve el número de secuencia de asignación en `plRequestNumber`. Este número representa el orden en el que se asignó el bloque en relación con todos los demás **nueva** asignaciones.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxisvalidaddress"></a>AfxIsValidAddress  
 Pruebas de cualquier dirección de memoria para asegurarse de que se encuentra totalmente dentro de espacio de memoria del programa.  
  
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
 Contiene el número de bytes de memoria se va a probar.  
  
 *bReadWrite*  
 Especifica si la memoria es tanto de lectura y escritura ( **TRUE**) o simplemente leyendo ( **FALSE**).  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, distinto de cero si el bloque de memoria especificado está dentro de completamente espacio de memoria del programa; en caso contrario es 0.  
  
 En las compilaciones de depuración no, distinto de cero si `lp` no es NULL; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La dirección no está restringida a bloques asignados por **nueva**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxisvalidstring"></a>AfxIsValidString  
 Utilice esta función para determinar si un puntero a una cadena es válido.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Puntero que se va a probar.  
  
 `nLength`  
 Especifica la longitud de la cadena que se va a probar, en bytes. Un valor de -1 indica que será la cadena terminada en null.  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, distinto de cero si el puntero especificado apunta a una cadena del tamaño especificado; en caso contrario es 0.  
  
 En las compilaciones de depuración no, distinto de cero si `lpsz` no es NULL; de lo contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities #29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxsetallochook"></a>AfxSetAllocHook  
 Establece un enlace que permite llamar a la función especificada antes de que se asigna cada bloque de memoria.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parámetros  
 *pfnAllocHook*  
 Especifica el nombre de la función se debe llamar. Vea la sección Comentarios para el prototipo de una función de asignación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si desea permitir la asignación; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El asignador de memoria de depuración de la biblioteca Microsoft Foundation Class puede llamar a una función de enlace definidos por el usuario para permitir al usuario para supervisar una asignación de memoria y para controlar si se permite la asignación. Funciones de enlace de asignación son un prototipo:  
  
 **BOOL AFXAPI AllocHook( size_t** `nSize`**, BOOL** `bObject`**, LONG** `lRequestNumber` **);**  
  
 `nSize`  
 El tamaño de la asignación de memoria propuesto.  
  
 `bObject`  
 **TRUE** si la asignación es para un `CObject`-objeto derivado; en caso contrario **FALSE**.  
  
 `lRequestNumber`  
 Número de secuencia de la asignación de memoria.  
  
 Tenga en cuenta que la **AFXAPI** convención de llamada implica que el destinatario debe quitar los parámetros de la pila.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxdoforallclasses"></a>AfxDoForAllClasses  
 Llama a la función de la iteración especificada para todos los serializable `CObject`-clases derivadas en el espacio de memoria de la aplicación.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pfn`  
 Señala a una función de la iteración a llamarse para cada clase. Los argumentos de función son un puntero a un `CRuntimeClass` objeto y un puntero void para los datos adicionales que proporciona el autor de la llamada a la función.  
  
 `pContext`  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Serializable `CObject`-clases derivadas son clases derivadas usando la `DECLARE_SERIAL` macro. El puntero que se pasa a `AfxDoForAllClasses` en `pContext` se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections #113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxdoforallobjects"></a>AfxDoForAllObjects  
 Ejecuta la función de la iteración especificada para todos los objetos derivan de `CObject` que hayan sido asignadas con **nueva**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pfn`  
 Señala a una función de iteración que se ejecuta para cada objeto. Los argumentos de función son un puntero a un `CObject` y un puntero void a los datos adicionales que proporciona el autor de la llamada a la función.  
  
 `pContext`  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 No se enumeran la pila, de forma global, o los objetos incrustados. El puntero se pasa a `AfxDoForAllObjects` en `pContext` se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections #115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
