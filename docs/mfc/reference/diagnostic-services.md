---
title: Servicios de diagnóstico | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5be60ff1f0aa8b2ceff7517a9af968e0b7690478
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214684"
---
# <a name="diagnostic-services"></a>Servicios de diagnóstico
La biblioteca MFC (Microsoft Foundation Class) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:  
  
-   Macros de diagnóstico generales  
  
-   Funciones y variables de diagnóstico general  
  
-   Funciones de diagnóstico de objetos  
  
 Estas macros y funciones están disponibles para todas las clases derivadas de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todas excepto DEBUG_NEW y comprobar no hacen nada en la versión de lanzamiento.  
  
 En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en el archivo de implementación, todas las llamadas a **nuevo** almacenarán el nombre de archivo y el número de línea en el que se realizó la asignación de memoria. La función [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) mostrará esta información adicional, lo que le permitirá identificar fugas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para información adicional sobre el resultado de diagnóstico.  
  
 Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para más información, vea [Rutinas de depuración](../../c-runtime-library/debug-routines.md) en la Referencia de la biblioteca en tiempo de ejecución.  
  
### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnóstico generales de MFC  
  
|||  
|-|-|  
|[ASSERT](#assert)|Imprime un mensaje y, a continuación, se anula el programa si la expresión especificada se evalúa como FALSE en la versión de depuración de la biblioteca.|  
|[ASSERT_KINDOF](#assert_kindof)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|  
|[ASSERT_VALID](#assert_valid)|Prueba la validez interna de un objeto llamando a su función de miembro `AssertValid` ; normalmente invalidada desde `CObject`.|
|[DEBUG_NEW](#debug_new)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|  
|[DEBUG_ONLY](#debug_only)|Similar a la aserción pero no prueba el valor de la expresión. resulta útil para el código que se debe ejecutar solo en modo de depuración.|  
|[Asegúrese de que y ENSURE_VALID](#ensure)|Usar para validar la corrección de datos.|
|[THIS_FILE](#this_file)|Expande el nombre del archivo que se está compilando.|
|[TRACE](#trace)|Ofrece capacidad similar a `printf`en la versión de depuración de la biblioteca.|  
|[VERIFY](#verify)|Similar a la aserción pero evalúa la expresión en la versión de lanzamiento de la biblioteca, así como en la versión de depuración.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funciones y variables de diagnóstico general de MFC  
  
|||  
|-|-|  
|[afxDump](#afxdump)|Variable global que envía información de [CDumpContext](../../mfc/reference/cdumpcontext-class.md) a la ventana de salida del depurador o al terminal de depuración.|  
|[afxMemDF](#afxmemdf)|Variable global que controla el comportamiento del asignador de memoria de depuración.|  
|[AfxCheckError](#afxcheckerror)|Variable global que se usa para probar la SCODE pasado para ver si es un error y, si es así, genera el error adecuado.|  
|[AfxCheckMemory](#afxcheckmemory)|Comprueba la integridad de toda la memoria asignada actualmente.|  
|[AfxDebugBreak](#afxdebugbreak)|Produce una interrupción en la ejecución.|
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
|[AfxDoForAllClasses](#afxdoforallclasses)|Realiza una función especificada en todas las clases derivadas por `CObject`que admiten la comprobación de tipos en tiempo de ejecución.|  
|[AfxDoForAllObjects](#afxdoforallobjects)|Realiza una función especificada en todos los objetos derivados por `CObject`asignados con **nuevo**.|  

### <a name="mfc-compilation-macros"></a>Macros de compilación de MFC
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Suprime las advertencias del compilador para el uso de funciones en desuso de MFC.|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS
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

## <a name="afxdebugbreak"></a> AfxDebugBreak
Llame a esta función para que se produzca una interrupción (en la ubicación de la llamada a `AfxDebugBreak`) en la ejecución de la versión de depuración de la aplicación MFC.  

### <a name="syntax"></a>Sintaxis    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Comentarios  
 `AfxDebugBreak` no tiene ningún efecto en las versiones de una aplicación MFC y debe quitarse. Esta función solo debe usarse en aplicaciones MFC. Use la versión de API de Win32, `DebugBreak`, para producir un salto en las aplicaciones no basados en MFC.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxver_.h   

##  <a name="assert"></a>  ASSERT
 Se evalúa como su argumento.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 *booleanExpression*  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como 0 o distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y anula el programa. Si la condición es distinto de cero, no hace nada.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen, y *num* es el número de línea de la aserción con error en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, ASSERT no se evalúa la expresión y, por tanto, no se interrumpirá el programa. Si la expresión debe evaluarse independientemente del entorno, utilice la macro VERIFY en lugar de ASSERT.  
  
> [!NOTE]
>  Esta función está disponible solo en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF  
 Esta macro se afirma que el objeto al que señala es un objeto de la clase especificada, o es un objeto de una clase que deriva de la clase especificada.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parámetros  
 *classname*  
 El nombre de un `CObject`-clase derivada.  
  
 *pObject*  
 Un puntero a un objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 El *pobject* parámetro debe ser un puntero a un objeto y puede ser **const**. El objeto señalado y debe ser compatible con la clase `CObject` información de clases en tiempo de ejecución. Por ejemplo, para asegurarse de que `pDocument` es un puntero a un objeto de la `CMyDoc` clase o cualquiera de sus derivados, podríamos codificar:  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Mediante el `ASSERT_KINDOF` macro es exactamente igual que la codificación:  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Esta función solo funciona en clases declaradas con el [DECLARE_DYNAMIC] (ejecución tiempo objeto modelo services.md #declare_dynamic o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.  
  
> [!NOTE]
>  Esta función está disponible solo en la versión de depuración de MFC.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID  
 Usar para probar sus suposiciones acerca de la validez del estado interno de un objeto.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parámetros  
 *pObject*  
 Especifica un objeto de una clase derivada de `CObject` que tiene una versión de reemplazo del `AssertValid` función miembro.  
  
### <a name="remarks"></a>Comentarios  
 ASSERT_VALID llamadas la `AssertValid` función de miembro del objeto pasado como argumento.  
  
 En la versión de lanzamiento de MFC, ASSERT_VALID no hace nada. En la versión de depuración, valida el puntero, se comprueba con valores NULL y se llama propia del objeto `AssertValid` funciones miembro. Si alguna de estas pruebas se produce un error, se muestra un mensaje de alerta en la misma manera que [ASSERT](#assert).  
  
> [!NOTE]
>  Esta función está disponible solo en la versión de depuración de MFC.  
  
 Para obtener más información y ejemplos, vea [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW  
 Ayuda a buscar pérdidas de memoria.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Comentarios  
 Puede usar DEBUG_NEW en todas partes en el programa que normalmente usaría el **nuevo** operador para asignar el almacenamiento de montón.  
  
 En modo de depuración (cuando el **_DEBUG** símbolo está definido), DEBUG_NEW realiza un seguimiento de lo nombre de archivo y número de línea para cada objeto que asigna. A continuación, cuando se usa el [CMemoryState:: DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) función miembro, se muestra cada objeto asignado con DEBUG_NEW con el nombre de archivo y número de línea donde fue asignado.  
  
 Para utilizar DEBUG_NEW, inserte la siguiente directiva en los archivos de origen:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Una vez que inserte esta directiva, el preprocesador insertará DEBUG_NEW siempre que utilice **nuevo**, y MFC encarga del resto. Al compilar una versión de lanzamiento del programa, DEBUG_NEW se resuelve como una simple **nuevo** operación y la información de número de línea y de nombre de archivo no se generan.  
  
> [!NOTE]
>  En versiones anteriores de MFC (4.1 y versiones anterior), era necesario colocar el `#define` instrucción después de todas las instrucciones que se llama a la macro IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL. Esto ya no es necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY  
 En modo de depuración (cuando el **_DEBUG** símbolo está definido), DEBUG_ONLY evalúa su argumento.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Comentarios  
 En una versión de lanzamiento, DEBUG_ONLY no evalúa su argumento. Esto es útil si tiene código que se debe ejecutar solo en compilaciones de depuración.  
  
 El debug_only (macro) es equivalente a la que rodean *expresión* con `#ifdef _DEBUG` y `#endif`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

 ### <a name="ensure"></a>  Asegúrese de que y ENSURE_VALID
Usar para validar la corrección de datos.  
   
### <a name="syntax"></a>Sintaxis    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Parámetros  
 *booleanExpression*  
 Especifica una expresión booleana que va a probarse.  
   
### <a name="remarks"></a>Comentarios  
 El propósito de estas macros es mejorar la validación de parámetros. Las macros impiden continuar el proceso de parámetros incorrectos en el código. A diferencia de las macros de aserción, las macros Asegúrese de iniciar una excepción además de generar una aserción.  
  
 Las macros se comportan de dos maneras, según la configuración del proyecto. Las macros de llamar a ASSERT y, a continuación, inicia una excepción si se produce un error en la aserción. Por lo tanto, en las configuraciones de depuración (es decir, donde se define _DEBUG) las macros generan una aserción y excepción en configuraciones de lanzamiento, el proceso de macros solo la excepción (ASSERT no evalúa la expresión en las configuraciones Release).  
  
 La macro ENSURE_ARG actúa como la macro Asegúrese.  
  
 ENSURE_VALID llama a la macro ASSERT_VALID (que tiene un efecto solo en compilaciones de depuración). Además, ENSURE_VALID produce una excepción si el puntero es NULL. Se realiza la prueba NULL en configuraciones Debug y Release.  
  
 Si se produce un error en cualquiera de estas pruebas, se muestra un mensaje de alerta en la misma manera que la aserción. La macro produce una excepción de argumento no válido si es necesario.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [COMPROBAR](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE
Expande el nombre del archivo que se está compilando.  
   
### <a name="syntax"></a>Sintaxis    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Comentarios  
 La información se utiliza por las macros de aserción y comprobar. Los asistentes de código y el Asistente para aplicaciones colocan la macro en los archivos de código fuente que creen.  
   
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
 [VERIFY](#verify)


##  <a name="trace"></a>  TRACE  
 Envía la cadena especificada para el depurador de la aplicación actual.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) para obtener una descripción del seguimiento. SEGUIMIENTO y ATLTRACE2 tienen el mismo comportamiento.  
  
 En la versión de depuración de MFC, esta macro envía la cadena especificada para el depurador de la aplicación actual. En una versión de lanzamiento, esta macro se compila en nothing (código no se genera en absoluto).  
  
 Para obtener más información, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="verify"></a>  VERIFY  
 En la versión de depuración de MFC, se evalúa como su argumento.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parámetros  
 *booleanExpression*  
 Especifica una expresión (incluidos los valores de puntero) que se evalúa como 0 o distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Si el resultado es 0, la macro imprime un mensaje de diagnóstico y detiene el programa. Si la condición es distinto de cero, no hace nada.  
  
 El mensaje de diagnóstico tiene la forma  
  
 `assertion failed in file <name> in line <num>`  
  
 donde *nombre* es el nombre del archivo de origen y *num* es el número de línea de la aserción con error en el archivo de origen.  
  
 En la versión de lanzamiento de MFC, compruebe evalúa la expresión pero no imprimir ni interrumpir el programa. Por ejemplo, si la expresión es una llamada de función, se realizará la llamada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (CDumpContext en MFC)  
 Proporciona funcionalidad básica de volcado de objetos en la aplicación.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Comentarios  
 `afxDump` está predefinido [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto que le permite enviar `CDumpContext` información en la ventana de salida del depurador o en un terminal de depuración. Por lo general, proporcionan `afxDump` como un parámetro a `CObject::Dump`.  
  
 En Windows NT y todas las versiones de Windows, `afxDump` salida se envía a la ventana de salida de depuración de Visual C++, cuando se depura la aplicación.  
  
 Esta variable solo se define en la versión de depuración de MFC. Para obtener más información sobre `afxDump`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h


## <a name="afxdump"></a> AfxDump (interno)
Función interna que utiliza MFC para volcar el estado de un objeto durante la depuración.  

### <a name="syntax"></a>Sintaxis    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Parámetros  
 *lugar de nacimiento*  
 Un puntero a un objeto de una clase derivada de `CObject`.  
   
### <a name="remarks"></a>Comentarios  
 `AfxDump` llama a un objeto `Dump` función miembro y envía la información a la ubicación especificada por el `afxDump` variable. `AfxDump` solo está disponible en la versión de depuración de MFC.  
  
 El código del programa no debe llamar a `AfxDump`, pero en su lugar, debe llamar a la `Dump` función de miembro del objeto correspondiente.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
   
### <a name="see-also"></a>Vea también  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxMemDF  
 Esta variable es accesible desde un depurador o el programa y permite ajustar el diagnóstico de asignación.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Comentarios  
 `afxMemDF` puede tener los valores siguientes según lo especificado por la enumeración `afxMemDF`:  
  
- `allocMemDF` Activa el asignador de depuración (valor predeterminado en la biblioteca de depuración).  
  
- `delayFreeMemDF` Retrasos de liberar memoria. Mientras el programa libera un bloque de memoria, el asignador no devuelve esa memoria para el sistema operativo subyacente. Esto colocará la carga máxima de memoria en el programa.  
  
- `checkAlwaysMemDF` Las llamadas `AfxCheckMemory` cada vez que se asigna o libera memoria. Esto ralentiza considerablemente las cancelaciones de asignación y asignaciones de memoria.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError  
 Esta función comprueba el SCODE pasado para ver si se trata de un error.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es un error, la función produce una excepción. Si el SCODE pasado es E_OUTOFMEMORY, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) mediante una llamada a [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). En caso contrario, la función produce un [COleException](../../mfc/reference/coleexception-class.md) mediante una llamada a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Esta función se puede usar para comprobar los valores devueltos de las llamadas a funciones OLE de la aplicación. Comprobando el valor devuelto con esta función en la aplicación puede reaccionar correctamente las condiciones de error con una cantidad mínima de código.  
  
> [!NOTE]
>  Esta función tiene el mismo efecto en modo de depuración y las compilaciones de no depuración.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory  
 Esta función valida el bloque de memoria libre e imprime los mensajes de error según sea necesario.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si no hay errores de memoria; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si la función detecta que no hay daños en la memoria, se imprime nada.  
  
 Se comprueban todos los bloques de memoria asignados actualmente en el montón, las asignadas por incluidas **nueva** pero no los asignado mediante llamadas directas a los asignadores de memoria subyacente, como el **malloc** función o el `GlobalAlloc` función de Windows. Si se encuentra ningún bloque está dañado, se imprime un mensaje en la salida del depurador.  
  
 Si incluye la línea  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 en un módulo de programa, las llamadas posteriores a `AfxCheckMemory` mostrar el nombre de archivo y número de línea donde se asignó la memoria.  
  
> [!NOTE]
>  Si el módulo contiene uno o más implementaciones de las clases serializables, a continuación, debe colocar el `#define` línea después de la última llamada de macro IMPLEMENT_SERIAL.  
  
 Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
 
##  <a name="afxdump"></a>  AfxDump (MFC)  
 Llame a esta función en el depurador para volcar el estado de un objeto durante la depuración.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parámetros  
 *lugar de nacimiento*  
 Un puntero a un objeto de una clase derivada de `CObject`.  
  
### <a name="remarks"></a>Comentarios  
 `AfxDump` llama a un objeto `Dump` función miembro y envía la información a la ubicación especificada por el `afxDump` variable. `AfxDump` solo está disponible en la versión de depuración de MFC.  
  
 El código del programa no debe llamar a `AfxDump`, pero en su lugar, debe llamar a la `Dump` función de miembro del objeto correspondiente.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  

### <a name="see-also"></a>Vea también  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  AfxDumpStack  
 Esta función global puede usarse para generar una imagen de la pila actual.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTarget*  
 Indica el destino de la salida de volcado de memoria. Los valores posibles que se pueden combinar con la operación bit a bit OR ( **&#124;**) (operador), son los siguientes:  
  
- AFX_STACK_DUMP_TARGET_TRACE envía la salida por medio de la [seguimiento](#trace) macro. La macro TRACE genera el resultado en las compilaciones de depuración solo; no genera ninguna salida en las compilaciones de versión. Además, se puede redirigir seguimiento a otros destinos además el depurador.  
  
- AFX_STACK_DUMP_TARGET_DEFAULT envía la salida de volcado de memoria en el destino predeterminado. Para una compilación de depuración, la salida se dirige a la macro TRACE. En una versión de lanzamiento, la salida se dirige en el Portapapeles.  
  
- AFX_STACK_DUMP_TARGET_CLIPBOARD envía la salida en el Portapapeles únicamente. Los datos se colocan en el Portapapeles como texto sin formato con el formato de Portapapeles CF_TEXT.  
  
- AFX_STACK_DUMP_TARGET_BOTH envía la salida en el Portapapeles y, a la macro TRACE, al mismo tiempo.  
  
- Salida AFX_STACK_DUMP_TARGET_ODS envía directamente al depurador por medio de la función de Win32 `OutputDebugString()`. Esta opción generará la salida del depurador en ambas versiones de depuración y compilaciones de versión cuando se adjunta un depurador al proceso. AFX_STACK_DUMP_TARGET_ODS siempre alcanza el depurador (si está conectado) y no se pueden redirigir.  
  
### <a name="remarks"></a>Comentarios  
 El ejemplo siguiente refleja una sola línea de la salida generada por llamar a `AfxDumpStack` desde un controlador de botón en una aplicación de cuadro de diálogo MFC:  
  
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
  
 Cada línea en la salida anterior indica la dirección de la última llamada de función, el nombre de ruta de acceso completa del módulo que contiene la llamada de función y el prototipo de función que llama. Si la llamada de función en la pila no se realiza en la dirección de la función exacta, se muestra un desplazamiento de bytes.  
  
 Por ejemplo, la tabla siguiente describe la primera línea de la salida anterior:  
  
|Salida|Descripción|  
|------------|-----------------|  
|`00427D55:`|La dirección de devolución de la última llamada de función.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|El nombre de ruta de acceso completa del módulo que contiene la llamada de función.|  
|`void AfxDumpStack(unsigned long)`|El prototipo de función se llama.|  
|`+ 181 bytes`|Desplazamiento en bytes de la dirección del prototipo de función (en este caso, `void AfxDumpStack(unsigned long)`) a la dirección de retorno (en este caso, `00427D55`).|  
  
 `AfxDumpStack` está disponible en versiones nondebug y depuración de las bibliotecas MFC; Sin embargo, la función siempre está vinculada estáticamente, incluso cuando el archivo ejecutable usa MFC en un archivo DLL compartido. En las implementaciones de la biblioteca compartida, la función se encuentra en la MFCS42. Biblioteca LIB (y sus variantes).  
  
 Para usar correctamente esta función:  
  
-   El archivo IMAGEHLP. Archivo DLL debe estar en la ruta de acceso. Si no tiene este archivo DLL, la función mostrará un mensaje de error. Consulte [bibliotecas de Ayuda de la imagen](/windows/desktop/Debug/image-help-library) para obtener información sobre el conjunto de funciones proporcionado IMAGEHLP.  
  
-   Los módulos que tienen los marcos en la pila deben incluir información de depuración. Si no contienen información de depuración, la función seguirá generando un seguimiento de pila, pero el seguimiento será menos detallado.  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump  
 Habilita y deshabilita el volcado de pérdida de memoria en el destructor AFX_DEBUG_STATE.  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bDump*  
 TRUE indica que el volcado de pérdida de memoria está habilitado; FALSE indica que el volcado de pérdida de memoria está deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor anterior de esta marca.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación descarga la biblioteca MFC, esta comprueba si hay pérdidas de memoria. En este momento, las pérdidas de memoria se notifican al usuario a través de la **depurar** ventana de Visual Studio.  
  
 Si la aplicación carga otra biblioteca antes que la biblioteca MFC, algunas asignaciones de memoria de la biblioteca se notificarán incorrectamente como pérdidas de memoria. Las pérdidas de memoria falsas pueden hacer que la aplicación se cierre lentamente, ya que la biblioteca MFC las estará notificando. En este caso, use `AfxEnableMemoryLeakDump` para deshabilitar el volcado de pérdida de memoria.  
  
> [!NOTE]
>  Si usa este método para desactivar el volcado de pérdida de memoria, no recibirá ningún informe de pérdidas de memoria válidas en la aplicación. Solo debe usar este método si está seguro de que el informe de pérdida de memoria contiene pérdidas de memoria falsas.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking  
 Normalmente está habilitada el seguimiento diagnóstico de la memoria en la versión de depuración de MFC.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parámetros  
 *bTrack*  
 Establecer este valor en TRUE, se en memoria de seguimiento; FALSE lo desactiva.  
  
### <a name="return-value"></a>Valor devuelto  
 La configuración anterior de la marca de habilitación del seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para deshabilitar el seguimiento en las secciones del código que sabe que son los bloques se asignan correctamente.  
  
 Para obtener más información sobre `AfxEnableMemoryTracking`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock  
 Comprueba una dirección de memoria para asegurarse de que representa un bloque de memoria activo que se ha asignado por la versión de diagnóstico **nuevo**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Apunta a un bloque de memoria que va a probarse.  
  
 *nBytes*  
 Contiene la longitud del bloque de memoria en bytes.  
  
 *plRequestNumber*  
 Apunta a un **largo** entero que se rellenará con el número de secuencia de asignación del bloque de memoria, o cero si no representa un bloque de memoria activo actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el bloque de memoria está asignado actualmente y la longitud es correcta. en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 También comprueba el tamaño especificado en el tamaño asignado original. Si la función devuelve cero, se devuelve el número de secuencia de asignación en *plRequestNumber*. Este número representa el orden en que se asignó el bloque en relación con todos los demás **nuevo** asignaciones.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress  
 Las pruebas en cualquier dirección de memoria para asegurarse de que se está incluido completamente en el espacio de memoria del programa.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Parámetros  
 *LP*  
 Apunta a la dirección de memoria que va a probarse.  
  
 *nBytes*  
 Contiene el número de bytes de memoria que va a probarse.  
  
 *bReadWrite*  
 Especifica si la memoria es tanto para lectura y escritura (TRUE) o solo lectura (FALSE).  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, distinto de cero si bloquea la memoria especificada está dentro de su totalidad espacio de memoria del programa; en caso contrario, es 0.  
  
 En versiones no depuradas, cero si *lp* no es NULL; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La dirección no está restringida a bloques asignados por **nuevo**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxisvalidstring"></a>  AfxIsValidString  
 Utilice esta función para determinar si un puntero a una cadena es válido.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parámetros  
 *lpsz*  
 Puntero que se va a probar.  
  
 *nLength*  
 Especifica la longitud de la cadena que se va a probar, en bytes. El valor -1 indica que será la cadena terminada en null.  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, distinto de cero si el puntero especificado apunta a una cadena del tamaño especificado; en caso contrario, es 0.  
  
 En versiones no depuradas, cero si *lpsz* no es NULL; de lo contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxsetallochook"></a>  AfxSetAllocHook  
 Establece un enlace que permite realizar la llamada de la función especificada antes de que se asigna cada bloque de memoria.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parámetros  
 *pfnAllocHook*  
 Especifica el nombre de la función para llamar a. Vea los comentarios sobre el prototipo de una función de asignación.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si desea permitir la asignación; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El asignador de memoria de depuración de la biblioteca Microsoft Foundation Class puede llamar a una función de enlace definido por el usuario para permitir al usuario para supervisar una asignación de memoria y para controlar si se permite la asignación. Funciones de enlace de asignación son prototipos como sigue:  
  
 **BOOL AFXAPI AllocHook (size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**  
  
 *nSize*  
 El tamaño de la asignación de memoria propuesto.  
  
 *bEmpaquetador*  
 TRUE si la asignación es para un `CObject`-objeto derivado; de lo contrario, FALSE.  
  
 *lRequestNumber*  
 Número de secuencia de la asignación de memoria.  
  
 Tenga en cuenta que la convención de llamada de AFXAPI implica que el destinatario debe quitar los parámetros de la pila.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses  
 Llama a la función de la iteración especificada para serializar `CObject`-clases derivadas en el espacio de memoria de la aplicación.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 *PFN*  
 Señala a una función de la iteración que se llama para cada clase. Los argumentos de función son un puntero a un `CRuntimeClass` objeto y un puntero void para los datos adicionales que proporciona el autor de la llamada a la función.  
  
 *pContext*  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser NULL.  
  
### <a name="remarks"></a>Comentarios  
 Serializable `CObject`-las clases derivadas son clases derivadas de utilizar la macro DECLARE_SERIAL. El puntero que se pasa a `AfxDoForAllClasses` en *pContext* se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects  
 Ejecuta la función de la iteración especificada para todos los objetos derivan de `CObject` que se han asignado con **nuevo**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parámetros  
 *PFN*  
 Señala una función de iteración para ejecutar para cada objeto. Los argumentos de función son un puntero a un `CObject` y un puntero void para los datos adicionales que proporciona el autor de la llamada a la función.  
  
 *pContext*  
 Puntos de datos opcionales que puede proporcionar el autor de la llamada a la función de la iteración. Este puntero puede ser NULL.  
  
### <a name="remarks"></a>Comentarios  
 No se enumeran pila, global, o los objetos incrustados. El puntero se pasa a `AfxDoForAllObjects` en *pContext* se pasa a la función de la iteración especificada cada vez que se llama.  
  
> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)