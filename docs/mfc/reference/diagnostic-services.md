---
title: Servicios de diagnóstico
ms.date: 11/04/2016
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
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365791"
---
# <a name="diagnostic-services"></a>Servicios de diagnóstico

La biblioteca MFC (Microsoft Foundation Class) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:

- Macros de diagnóstico generales

- Funciones y variables de diagnóstico general

- Funciones de diagnóstico de objetos

Estas macros y funciones están disponibles para todas las clases derivadas de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todos excepto DEBUG_NEW y VERIFY no hacen nada en la versión Release.

En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

en el archivo de implementación, todas las llamadas a **new** almacenarán el nombre de archivo y el número de línea donde tuvo lugar la asignación de memoria. La función [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) mostrará esta información adicional, lo que le permite identificar pérdidas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para obtener información adicional sobre la salida de diagnóstico.

Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para obtener más información, consulte Rutinas de [depuración](../../c-runtime-library/debug-routines.md) en la Referencia de la biblioteca en tiempo de ejecución.

### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnóstico generales de MFC

|||
|-|-|
|[Afirmar](#assert)|Imprime un mensaje y luego anula el programa si la expresión especificada se evalúa como FALSE en la versión de depuración de la biblioteca.|
|[ASSERT_KINDOF](#assert_kindof)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|
|[ASSERT_VALID](#assert_valid)|Prueba la validez interna de un objeto llamando a su función de miembro `AssertValid` ; normalmente invalidada desde `CObject`.|
|[DEBUG_NEW](#debug_new)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|
|[DEBUG_ONLY](#debug_only)|Similar a ASSERT pero no prueba el valor de la expresión; útil para código que se debe ejecutar solo en modo de depuración.|
|[ASEGURAR y ENSURE_VALID](#ensure)|Se utiliza para validar la corrección de datos.|
|[THIS_FILE](#this_file)|Se expande al nombre del archivo que se está compilando.|
|[Rastro](#trace)|Ofrece capacidad similar a `printf`en la versión de depuración de la biblioteca.|
|[Verificar](#verify)|Similar a ASSERT pero evalúa la expresión en la versión de lanzamiento de la biblioteca, así como en la versión de depuración.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funciones y variables de diagnóstico general de MFC

|||
|-|-|
|[afxDump](#afxdump)|Variable global que envía información [CDumpContext](../../mfc/reference/cdumpcontext-class.md) a la ventana de salida del depurador o al terminal de depuración.|
|[afxMemDF](#afxmemdf)|Variable global que controla el comportamiento del asignador de memoria de depuración.|
|[AfxCheckError](#afxcheckerror)|Variable global que se usa para probar el SCODE pasado para ver si es un error y, si es así, genera el error correspondiente.|
|[AfxCheckMemory](#afxcheckmemory)|Comprueba la integridad de toda la memoria asignada actualmente.|
|[AfxDebugBreak](#afxdebugbreak)|Provoca una interrupción en la ejecución.|
|[afxDump](#cdumpcontext_in_mfc)|Si se llama mientras se encuentra en el depurador, vuelca el estado de un objeto durante la depuración.|
|[afxDump](#afxdump)|Función interna que vuelca el estado de un objeto durante la depuración.|
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

### <a name="mfc-compilation-macros"></a>Macros de compilación MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Suprime las advertencias del compilador para el uso de funciones MFC en desuso.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Suprime las advertencias del compilador para el uso de funciones MFC en desuso.

### <a name="syntax"></a>Sintaxis

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Ejemplo

Este ejemplo de código provocaría una advertencia del compilador si no se definieran _AFX_SECURE_NO_WARNINGS.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a> AfxDebugBreak

Llame a esta función para provocar un `AfxDebugBreak`salto (en la ubicación de la llamada a ) en la ejecución de la versión de depuración de la aplicación MFC.

### <a name="syntax"></a>Sintaxis

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Observaciones

`AfxDebugBreak`no tiene ningún efecto en las versiones de lanzamiento de una aplicación MFC y debe quitarse. Esta función solo se debe utilizar en aplicaciones MFC. Utilice la versión de `DebugBreak`la API de Win32, para provocar una interrupción en las aplicaciones que no son MFC.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxver_.h

## <a name="assert"></a><a name="assert"></a>Afirmar

Evalúa su argumento.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión (incluidos los valores de puntero) que se evalúa como distinto de cero o 0.

### <a name="remarks"></a>Observaciones

Si el resultado es 0, la macro imprime un mensaje de diagnóstico y anula el programa. Si la condición es distinta de cero, no hace nada.

El mensaje de diagnóstico tiene la forma

`assertion failed in file <name> in line <num>`

donde *name* es el nombre del archivo de origen y *num* es el número de línea de la aserción que produjo un error en el archivo de origen.

En la versión Release de MFC, ASSERT no evalúa la expresión y, por lo tanto, no interrumpirá el programa. Si la expresión debe evaluarse independientemente del entorno, utilice la macro VERIFY en lugar de ASSERT.

> [!NOTE]
> Esta función solo está disponible en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

Esta macro afirma que el objeto al que se apunta es un objeto de la clase especificada o es un objeto de una clase derivada de la clase especificada.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parámetros

*Classname*<br/>
El nombre `CObject`de una clase derivada.

*pobject*<br/>
Puntero a un objeto de clase.

### <a name="remarks"></a>Observaciones

El parámetro *pobject* debe ser un puntero a un objeto y puede ser **const**. El objeto al que se `CObject` apunta y la clase debe admitir información de clase en tiempo de ejecución. Por ejemplo, para `pDocument` asegurarse de que es `CMyDoc` un puntero a un objeto de la clase, o cualquiera de sus derivados, podría codificar:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

El `ASSERT_KINDOF` uso de la macro es exactamente lo mismo que la codificación:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Esta función solo funciona para las clases declaradas con la macro [DECLARE_DYNAMIC](run-time-object-model-services.md-declare_dynamic o [DECLARE_SERIAL.](run-time-object-model-services.md#declare_serial)

> [!NOTE]
> Esta función solo está disponible en la versión de depuración de MFC.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

Se utiliza para probar sus suposiciones sobre la validez del estado interno de un objeto.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Especifica un objeto de una `CObject` clase derivada de que `AssertValid` tiene una versión de reemplazo de la función miembro.

### <a name="remarks"></a>Observaciones

ASSERT_VALID llama `AssertValid` a la función miembro del objeto pasado como argumento.

En la versión de versión de MFC, ASSERT_VALID no hace nada. En la versión de depuración, valida el puntero, comprueba en `AssertValid` NULL y llama a las propias funciones miembro del objeto. Si se produce un error en alguna de estas pruebas, se muestra un mensaje de alerta de la misma manera que [ASSERT](#assert).

> [!NOTE]
> Esta función solo está disponible en la versión de depuración de MFC.

Para obtener más información y ejemplos, vea [Depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>DEBUG_NEW

Ayuda a encontrar fugas de memoria.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Observaciones

Puede usar DEBUG_NEW en todas partes del programa que normalmente usaría el **operador new** para asignar almacenamiento en montgente.

En el modo de depuración (cuando se define el símbolo **de _DEBUG),** DEBUG_NEW realiza un seguimiento del nombre de archivo y el número de línea de cada objeto que asigna. A continuación, cuando se utiliza la Función miembro [CMemoryState::DumpAllObjectsSince,](cmemorystate-structure.md#dumpallobjectssince) cada objeto asignado con DEBUG_NEW se muestra con el nombre de archivo y el número de línea donde se asignó.

Para utilizar DEBUG_NEW, inserte la siguiente directiva en los archivos de origen:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Una vez que inserte esta directiva, el preprocesador insertará DEBUG_NEW dondequiera que use **new**y MFC hará el resto. Al compilar una versión de lanzamiento del programa, DEBUG_NEW se resuelve en una **nueva** operación simple y no se generan la información del nombre de archivo y del número de línea.

> [!NOTE]
> En versiones anteriores de MFC (4.1 y `#define` versiones anteriores) era necesario colocar la instrucción después de todas las instrucciones que llamaron a las macros IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL. Ya no es necesario.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

En el modo de depuración (cuando se define el símbolo **de _DEBUG),** DEBUG_ONLY evalúa su argumento.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Observaciones

En una compilación de versión, DEBUG_ONLY no evalúa su argumento. Esto es útil cuando tiene código que se debe ejecutar solo en compilaciones de depuración.

La macro DEBUG_ONLY es equivalente `#ifdef _DEBUG` `#endif`a la *expresión* circundante con y .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>ASEGURAR y ENSURE_VALID

Se utiliza para validar la corrección de datos.

### <a name="syntax"></a>Sintaxis

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión booleana que se va a probar.

### <a name="remarks"></a>Observaciones

El propósito de estas macros es mejorar la validación de parámetros. Las macros impiden el procesamiento posterior de parámetros incorrectos en el código. A diferencia de las macros ASSERT, las macros ENSURE producen una excepción además de generar una aserción.

Las macros se comportan de dos maneras, según la configuración del proyecto. Las macros llaman a ASSERT y, a continuación, producen una excepción si se produce un error en la aserción. Por lo tanto, en las configuraciones de depuración (es decir, donde se define _DEBUG) las macros producen una aserción y una excepción mientras que en las configuraciones de versión, las macros producen solo la excepción (ASSERT no evalúa la expresión en las configuraciones de versión).

La macro ENSURE_ARG actúa como la macro ENSURE.

ENSURE_VALID llama a la macro ASSERT_VALID (que solo tiene efecto en compilaciones de depuración). Además, ENSURE_VALID produce una excepción si el puntero es NULL. La prueba NULL se realiza en las configuraciones de depuración y versión.

Si se produce un error en alguna de estas pruebas, se muestra un mensaje de alerta de la misma manera que ASSERT. La macro produce una excepción de argumento no válido si es necesario.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

Se expande al nombre del archivo que se está compilando.

### <a name="syntax"></a>Sintaxis

```
THIS_FILE
```

### <a name="remarks"></a>Observaciones

La información es utilizada por las macros ASSERT y VERIFY. El Asistente para aplicaciones y los asistentes de código colocan la macro en los archivos de código fuente que crean.

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

## <a name="trace"></a><a name="trace"></a>Rastro

Envía la cadena especificada al depurador de la aplicación actual.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Observaciones

Consulte [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) para obtener una descripción de TRACE. TRACE y ATLTRACE2 tienen el mismo comportamiento.

En la versión de depuración de MFC, esta macro envía la cadena especificada al depurador de la aplicación actual. En una versión de lanzamiento, esta macro se compila en nada (no se genera ningún código en absoluto).

Para obtener más información, vea [Depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="verify"></a><a name="verify"></a>Verificar

En la versión de depuración de MFC, evalúa su argumento.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión (incluidos los valores de puntero) que se evalúa como distinto de cero o 0.

### <a name="remarks"></a>Observaciones

Si el resultado es 0, la macro imprime un mensaje de diagnóstico y detiene el programa. Si la condición es distinta de cero, no hace nada.

El mensaje de diagnóstico tiene la forma

`assertion failed in file <name> in line <num>`

donde *name* es el nombre del archivo de origen y *num* es el número de línea de la aserción que produjo un error en el archivo de origen.

En la versión Release de MFC, VERIFY evalúa la expresión pero no imprime ni interrumpe el programa. Por ejemplo, si la expresión es una llamada de función, se realizará la llamada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext en MFC)

Proporciona la capacidad básica de volcado de objetos en la aplicación.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Observaciones

`afxDump`es un objeto [CDumpContext](../../mfc/reference/cdumpcontext-class.md) predefinido que `CDumpContext` permite enviar información a la ventana de salida del depurador o a un terminal de depuración. Normalmente, se `afxDump` proporciona como `CObject::Dump`parámetro a .

En Windows NT y todas `afxDump` las versiones de Windows, la salida se envía a la ventana Desdepurar de salida de Visual C++ al depurar la aplicación.

Esta variable solo se define en la versión de depuración de MFC. Para obtener `afxDump`más información sobre , vea [Depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump (Interno)

Función interna que MFC utiliza para volcar el estado de un objeto durante la depuración.

### <a name="syntax"></a>Sintaxis

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*Pob*<br/>
Puntero a un objeto de una `CObject`clase derivada de .

### <a name="remarks"></a>Observaciones

`AfxDump`llama a la `Dump` función miembro de un objeto y `afxDump` envía la información a la ubicación especificada por la variable. `AfxDump`solo está disponible en la versión de depuración de MFC.

El código del `AfxDump`programa no debe `Dump` llamar a , sino que debe llamar a la función miembro del objeto adecuado.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

Esta variable es accesible desde un depurador o el programa y le permite ajustar los diagnósticos de asignación.

```
int  afxMemDF;
```

### <a name="remarks"></a>Observaciones

`afxMemDF`puede tener los siguientes valores según lo especificado por la enumeración: `afxMemDF`

- `allocMemDF`Activa la depuración del asignador (configuración predeterminada en la biblioteca de depuración).

- `delayFreeMemDF`Retrasos liberando memoria. Mientras el programa libera un bloque de memoria, el asignador no devuelve esa memoria al sistema operativo subyacente. Esto pondrá el máximo estrés de memoria en su programa.

- `checkAlwaysMemDF`Llamadas `AfxCheckMemory` cada vez que se asigna o libera memoria. Esto ralentizará significativamente las asignaciones de memoria y las desasignaciones.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError

Esta función prueba el SCODE pasado para ver si se trata de un error.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Observaciones

Si se trata de un error, la función produce una excepción. Si el SCODE pasado es E_OUTOFMEMORY, la función produce una [excepción](../../mfc/reference/cmemoryexception-class.md) a [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). De lo contrario, la función produce un [COleException](../../mfc/reference/coleexception-class.md) mediante una llamada a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Esta función se puede usar para comprobar los valores devueltos de las llamadas a funciones OLE en la aplicación. Al probar el valor devuelto con esta función en la aplicación, puede reaccionar correctamente a las condiciones de error con una cantidad mínima de código.

> [!NOTE]
> Esta función tiene el mismo efecto en las compilaciones de depuración y no depuración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory

Esta función valida el grupo de memoria libre e imprime mensajes de error según sea necesario.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no hay errores de memoria; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si la función no detecta daños en la memoria, no imprime nada.

Se comprueban todos los bloques de memoria asignados actualmente en el montón, incluidos los asignados por `GlobalAlloc` **nuevos** pero no los asignados por llamadas directas a asignadores de memoria subyacentes, como la función **malloc** o la función De Windows. Si se encuentra que algún bloque está dañado, se imprime un mensaje en la salida del depurador.

Si incluye la línea

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

en un módulo de programa, a continuación, las llamadas posteriores para `AfxCheckMemory` mostrar el nombre de archivo y el número de línea donde se asignó la memoria.

> [!NOTE]
> Si el módulo contiene una o más implementaciones de `#define` clases serializables, debe colocar la línea después de la última llamada de macro IMPLEMENT_SERIAL.

Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (MFC)

Llame a esta función mientras está en el depurador para volcar el estado de un objeto durante la depuración.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*Pob*<br/>
Puntero a un objeto de una `CObject`clase derivada de .

### <a name="remarks"></a>Observaciones

`AfxDump`llama a la `Dump` función miembro de un objeto y `afxDump` envía la información a la ubicación especificada por la variable. `AfxDump`solo está disponible en la versión de depuración de MFC.

El código del `AfxDump`programa no debe `Dump` llamar a , sino que debe llamar a la función miembro del objeto adecuado.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

Esta función global se puede utilizar para generar una imagen de la pila actual.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parámetros

*dwTarget*<br/>
Indica el destino de la salida de volcado. Los valores posibles, que se pueden combinar mediante el operador OR **(&#124;**) bit a bit, son los siguientes:

- AFX_STACK_DUMP_TARGET_TRACE Envía la salida mediante la macro [TRACE.](#trace) La macro TRACE genera la salida solo en compilaciones de depuración; no genera ninguna salida en las compilaciones de versión. Además, TRACE se puede redirigir a otros destinos además del depurador.

- AFX_STACK_DUMP_TARGET_DEFAULT Envía la salida de volcado al destino predeterminado. Para una compilación de depuración, la salida va a la macro TRACE. En una compilación de versión, la salida va al Portapapeles.

- AFX_STACK_DUMP_TARGET_CLIPBOARD Envía la salida solo al Portapapeles. Los datos se colocan en el Portapapeles como texto sin formato con el formato CF_TEXT Portapapeles.

- AFX_STACK_DUMP_TARGET_BOTH Envía la salida al Portapapeles y a la macro TRACE simultáneamente.

- AFX_STACK_DUMP_TARGET_ODS Envía la salida directamente al depurador `OutputDebugString()`mediante la función Win32 . Esta opción generará la salida del depurador en las compilaciones de depuración y versión cuando se adjunta un depurador al proceso. AFX_STACK_DUMP_TARGET_ODS siempre llega al depurador (si está asociado) y no se puede redirigir.

### <a name="remarks"></a>Observaciones

El ejemplo siguiente refleja una sola línea de `AfxDumpStack` la salida generada a partir de la llamada desde un controlador de botones en una aplicación de cuadro de diálogo MFC:

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

Cada línea de la salida anterior indica la dirección de la última llamada de función, el nombre de ruta de acceso completo del módulo que contiene la llamada de función y el prototipo de función llamado. Si la llamada de función en la pila no se produce en la dirección exacta de la función, se muestra un desplazamiento de bytes.

Por ejemplo, en la tabla siguiente se describe la primera línea de la salida anterior:

|Output|Descripción|
|------------|-----------------|
|`00427D55:`|La dirección de devolución de la última llamada de función.|
|`DUMP2\DEBUG\DUMP2.EXE!`|El nombre de ruta de acceso completo del módulo que contiene la llamada de función.|
|`void AfxDumpStack(unsigned long)`|Se llamó al prototipo de función.|
|`+ 181 bytes`|Desplazamiento en bytes desde la dirección del prototipo `void AfxDumpStack(unsigned long)`de función (en este `00427D55`caso, ) a la dirección de retorno (en este caso, ).|

`AfxDumpStack`está disponible en las versiones de depuración y no depuración de las bibliotecas MFC; sin embargo, la función siempre se vincula estáticamente, incluso cuando el archivo ejecutable utiliza MFC en un archivo DLL compartido. En las implementaciones de biblioteca compartida, la función se encuentra en MFCS42. Biblioteca LIB (y sus variantes).

Para utilizar esta función correctamente:

- El archivo IMAGEHLP. DLL debe estar en la ruta de acceso. Si no tiene este archivo DLL, la función mostrará un mensaje de error. Consulte Biblioteca de [ayuda](/windows/win32/Debug/image-help-library) de imágenes para obtener información sobre el conjunto de funciones proporcionado por IMAGEHLP.

- Los módulos que tienen tramas en la pila deben incluir información de depuración. Si no contienen información de depuración, la función seguirá generando un seguimiento de pila, pero el seguimiento será menos detallado.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Habilita y deshabilita el volcado de pérdida de memoria en el destructor AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parámetros

*bDump*<br/>
[en] TRUE indica que el volcado de pérdida de memoria está habilitado; FALSE indica que el volcado de pérdida de memoria está deshabilitado.

### <a name="return-value"></a>Valor devuelto

Valor anterior de esta marca.

### <a name="remarks"></a>Observaciones

Cuando una aplicación descarga la biblioteca MFC, esta comprueba si hay pérdidas de memoria. En este momento, las pérdidas de memoria se notifican al usuario a través de la ventana **Depurar** de Visual Studio.

Si la aplicación carga otra biblioteca antes que la biblioteca MFC, algunas asignaciones de memoria de la biblioteca se notificarán incorrectamente como pérdidas de memoria. Las pérdidas de memoria falsas pueden hacer que la aplicación se cierre lentamente, ya que la biblioteca MFC las estará notificando. En este caso, use `AfxEnableMemoryLeakDump` para deshabilitar el volcado de pérdida de memoria.

> [!NOTE]
> Si usa este método para desactivar el volcado de pérdida de memoria, no recibirá ningún informe de pérdidas de memoria válidas en la aplicación. Solo debe usar este método si está seguro de que el informe de pérdida de memoria contiene pérdidas de memoria falsas.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking

El seguimiento de memoria de diagnóstico normalmente está habilitado en la versión de depuración de MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parámetros

*bTrack*<br/>
Establecer este valor en TRUE activa el seguimiento de memoria; FALSE lo desactiva.

### <a name="return-value"></a>Valor devuelto

La configuración anterior de la marca de activación de seguimiento.

### <a name="remarks"></a>Observaciones

Utilice esta función para deshabilitar el seguimiento en secciones del código que sabe que están asignando bloques correctamente.

Para obtener `AfxEnableMemoryTracking`más información sobre , vea [Depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock

Comprueba una dirección de memoria para asegurarse de que representa un bloque de memoria activo actualmente asignado por la versión de diagnóstico de **new**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Apunta al bloque de memoria que se va a probar.

*nBytes*<br/>
Contiene la longitud del bloque de memoria en bytes.

*plRequestNumber*<br/>
Apunta a un entero **largo** que se rellenará con el número de secuencia de asignación del bloque de memoria, o cero si no representa un bloque de memoria activo actualmente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el bloque de memoria está asignado actualmente y la longitud es correcta; de lo contrario 0.

### <a name="remarks"></a>Observaciones

También comprueba el tamaño especificado con respecto al tamaño asignado original. Si la función devuelve distinto de cero, el número de secuencia de asignación se devuelve en *plRequestNumber*. Este número representa el orden en el que se asignó el bloque en relación con todas las demás asignaciones **nuevas.**

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress

Comprueba cualquier dirección de memoria para asegurarse de que está contenida completamente dentro del espacio de memoria del programa.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parámetros

*Lp*<br/>
Apunta a la dirección de memoria que se va a probar.

*nBytes*<br/>
Contiene el número de bytes de memoria que se van a probar.

*bReadWrite*<br/>
Especifica si la memoria es tanto para lectura como para escritura (TRUE) o simplemente para leer (FALSE).

### <a name="return-value"></a>Valor devuelto

En compilaciones de depuración, distinto de cero si el bloque de memoria especificado está contenido completamente dentro del espacio de memoria del programa; de lo contrario 0.

En compilaciones que no son de depuración, distinto de cero si *lp* no es NULL; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La dirección no está restringida a los bloques asignados por **new**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString

Utilice esta función para determinar si un puntero a una cadena es válido.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
El puntero que se va a probar.

*nLongitud*<br/>
Especifica la longitud de la cadena que se va a probar, en bytes. Un valor de -1 indica que la cadena estará terminada en null.

### <a name="return-value"></a>Valor devuelto

En compilaciones de depuración, distinto de cero si el puntero especificado apunta a una cadena del tamaño especificado; de lo contrario 0.

En compilaciones que no son de depuración, distinto de cero si *lpsz* no es NULL; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook

Establece un enlace que habilita la llamada de la función especificada antes de asignar cada bloque de memoria.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parámetros

*pfnAllocHook*<br/>
Especifica el nombre de la función a la que se va a llamar. Consulte las Observaciones para el prototipo de una función de asignación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si desea permitir la asignación; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El asignador de memoria de depuración de Microsoft Foundation Class Library puede llamar a una función de enlace definida por el usuario para permitir al usuario supervisar una asignación de memoria y controlar si se permite la asignación. Las funciones de gancho de asignación se crean como prototipos de la siguiente manera:

**BOOL AFXAPI AllocHook( size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**

*nTamaño*<br/>
El tamaño de la asignación de memoria propuesta.

*bObject*<br/>
TRUESi la asignación `CObject`es para un objeto derivado; de lo contrario FALSO.

*lRequestNumber*<br/>
Número de secuencia de asignación de memoria.

Tenga en cuenta que la convención de llamada AFXAPI implica que el destinatario debe quitar los parámetros de la pila.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses

Llama a la función de `CObject`iteración especificada para todas las clases derivadas serializables en el espacio de memoria de la aplicación.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Apunta a una función de iteración que se llamará para cada clase. Los argumentos de función `CRuntimeClass` son un puntero a un objeto y un puntero void a datos adicionales que el llamador proporciona a la función.

*pContext*<br/>
Señala a los datos opcionales que el autor de la llamada puede proporcionar a la función de iteración. Este puntero puede ser NULL.

### <a name="remarks"></a>Observaciones

Las `CObject`clases derivadas serializables son clases derivadas mediante la macro DECLARE_SERIAL. El puntero que `AfxDoForAllClasses` se pasa en *pContext* se pasa a la función de iteración especificada cada vez que se llama.

> [!NOTE]
> Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects

Ejecuta la función de iteración `CObject` especificada para todos los objetos derivados de los que se han asignado con **new**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Apunta a una función de iteración que se va a ejecutar para cada objeto. Los argumentos de función `CObject` son un puntero a a y un puntero void a datos adicionales que el llamador suministra a la función.

*pContext*<br/>
Señala a los datos opcionales que el autor de la llamada puede proporcionar a la función de iteración. Este puntero puede ser NULL.

### <a name="remarks"></a>Observaciones

Los objetos de pila, globales o incrustados no se enumeran. El puntero `AfxDoForAllObjects` que se pasa en *pContext* se pasa a la función de iteración especificada cada vez que se llama.

> [!NOTE]
> Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
