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
ms.openlocfilehash: 4cf3f53d1e238218b4eb892dc92e3c823dcc1296
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426754"
---
# <a name="diagnostic-services"></a>Servicios de diagnóstico

La biblioteca MFC (Microsoft Foundation Class) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:

- Macros de diagnóstico generales

- Funciones y variables de diagnóstico general

- Funciones de diagnóstico de objetos

Estas macros y funciones están disponibles para todas las clases derivadas de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todos excepto DEBUG_NEW y VERIFY no hacen nada en la versión de lanzamiento.

En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

en el archivo de implementación, todas las llamadas a **nuevo** almacenarán el nombre de archivo y el número de línea en el que se realizó la asignación de memoria. La función [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) mostrará esta información adicional, lo que le permitirá identificar fugas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para información adicional sobre el resultado de diagnóstico.

Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para más información, vea [Rutinas de depuración](../../c-runtime-library/debug-routines.md) en la Referencia de la biblioteca en tiempo de ejecución.

### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnóstico generales de MFC

|||
|-|-|
|[ASSERT](#assert)|Imprime un mensaje y luego anula el programa si la expresión especificada se evalúa como FALSE en la versión de depuración de la biblioteca.|
|[ASSERT_KINDOF](#assert_kindof)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|
|[ASSERT_VALID](#assert_valid)|Prueba la validez interna de un objeto llamando a su función de miembro `AssertValid` ; normalmente invalidada desde `CObject`.|
|[DEBUG_NEW](#debug_new)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|
|[DEBUG_ONLY](#debug_only)|Similar a ASSERT pero no prueba el valor de la expresión; útil para código que se debe ejecutar solo en modo de depuración.|
|[ASEGURARSE y ENSURE_VALID](#ensure)|Use para validar la exactitud de los datos.|
|[THIS_FILE](#this_file)|Se expande hasta el nombre del archivo que se está compilando.|
|[TRACE](#trace)|Ofrece capacidad similar a `printf`en la versión de depuración de la biblioteca.|
|[VERIFY](#verify)|Similar a ASSERT pero evalúa la expresión en la versión de lanzamiento de la biblioteca, así como en la versión de depuración.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funciones y variables de diagnóstico general de MFC

|||
|-|-|
|[afxDump](#afxdump)|Variable global que envía información de [CDumpContext](../../mfc/reference/cdumpcontext-class.md) a la ventana de salida del depurador o al terminal de depuración.|
|[afxMemDF](#afxmemdf)|Variable global que controla el comportamiento del asignador de memoria de depuración.|
|[AfxCheckError](#afxcheckerror)|Variable global que se usa para probar el SCODE pasado para ver si es un error y, si es así, genera el error correspondiente.|
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
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Suprime las advertencias del compilador para el uso de funciones de MFC en desuso.|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Suprime las advertencias del compilador para el uso de funciones de MFC en desuso.

### <a name="syntax"></a>Sintaxis

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Ejemplo

Este ejemplo de código produciría una advertencia del compilador si no se definieron _AFX_SECURE_NO_WARNINGS.

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

## <a name="afxdebugbreak"></a> AfxDebugBreak

Llame a esta función para producir una interrupción (en la ubicación de la llamada a `AfxDebugBreak`) en la ejecución de la versión de depuración de la aplicación MFC.

### <a name="syntax"></a>Sintaxis

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Observaciones

`AfxDebugBreak` no tiene ningún efecto en las versiones de lanzamiento de una aplicación MFC y debe quitarse. Esta función solo se debe usar en aplicaciones MFC. Use la versión de la API de Win32, `DebugBreak`, para producir una interrupción en aplicaciones no MFC.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxver_. h

##  <a name="assert"></a>  ASSERT

Evalúa su argumento.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión (incluidos los valores de puntero) que se evalúa como un valor distinto de cero o 0.

### <a name="remarks"></a>Observaciones

Si el resultado es 0, la macro imprime un mensaje de diagnóstico y anula el programa. Si la condición es distinto de cero, no hace nada.

El mensaje de diagnóstico tiene la forma

`assertion failed in file <name> in line <num>`

donde *Name* es el nombre del archivo de código fuente y *NUM* es el número de línea de la aserción que produjo un error en el archivo de código fuente.

En la versión de lanzamiento de MFC, Assert no evalúa la expresión y, por tanto, no interrumpirá el programa. Si la expresión se debe evaluar independientemente del entorno, use la macro VERIFY en lugar de Assert.

> [!NOTE]
>  Esta función solo está disponible en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

Esta macro afirma que el objeto al que se apunta es un objeto de la clase especificada o es un objeto de una clase derivada de la clase especificada.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parámetros

*classname*<br/>
Nombre de una clase derivada de `CObject`.

*pobject*<br/>
Un puntero a un objeto de clase.

### <a name="remarks"></a>Observaciones

El parámetro *pobject* debe ser un puntero a un objeto y puede ser **const**. El objeto al que se apunta y la clase deben admitir `CObject` la información de clase en tiempo de ejecución. Como ejemplo, para asegurarse de que `pDocument` es un puntero a un objeto de la clase `CMyDoc`, o a cualquiera de sus derivados, puede codificar:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

El uso de la macro `ASSERT_KINDOF` es exactamente igual que la codificación:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Esta función solo funciona para las clases declaradas con la macro [DECLARE_DYNAMIC] (Run-Time-Object-Model-Services. MD # declare_dynamic o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

> [!NOTE]
>  Esta función solo está disponible en la versión de depuración de MFC.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

Use para probar sus suposiciones sobre la validez del estado interno de un objeto.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Especifica un objeto de una clase derivada de `CObject` que tiene una versión de reemplazo de la función miembro `AssertValid`.

### <a name="remarks"></a>Observaciones

ASSERT_VALID llama a la función miembro `AssertValid` del objeto pasado como su argumento.

En la versión de lanzamiento de MFC, ASSERT_VALID no hace nada. En la versión de depuración, valida el puntero, comprueba con NULL y llama a las propias funciones miembro `AssertValid` del objeto. Si se produce un error en cualquiera de estas pruebas, se muestra un mensaje de alerta de la misma manera que la [aserción](#assert).

> [!NOTE]
>  Esta función solo está disponible en la versión de depuración de MFC.

Para obtener más información y ejemplos, vea [depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

Ayuda a buscar pérdidas de memoria.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Observaciones

Puede usar DEBUG_NEW en cualquier parte del programa que normalmente usaría el operador **New** para asignar el almacenamiento del montón.

En el modo de depuración (cuando se define el símbolo de **_DEBUG** ), DEBUG_NEW realiza un seguimiento del nombre de archivo y el número de línea para cada objeto que asigna. A continuación, cuando se usa la función miembro [CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) , cada objeto asignado con DEBUG_NEW se muestra con el nombre de archivo y el número de línea donde se asignó.

Para usar DEBUG_NEW, inserte la siguiente directiva en los archivos de código fuente:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Una vez insertada esta Directiva, el preprocesador insertará DEBUG_NEW siempre que use **New**y MFC realizará el resto. Al compilar una versión de lanzamiento del programa, DEBUG_NEW se resuelve en una operación **nueva** simple y no se generan la información del nombre de archivo y del número de línea.

> [!NOTE]
>  En versiones anteriores de MFC (4,1 y anteriores) era necesario colocar la instrucción `#define` después de todas las instrucciones que llamaran a las macros IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL. Ya no es necesario.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

En el modo de depuración (cuando se define el símbolo de **_DEBUG** ), DEBUG_ONLY evalúa su argumento.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Observaciones

En una compilación de versión, DEBUG_ONLY no evalúa su argumento. Esto resulta útil cuando se tiene código que debe ejecutarse solo en las compilaciones de depuración.

La macro DEBUG_ONLY es equivalente a la *expresión* circundante con `#ifdef _DEBUG` y `#endif`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

### <a name="ensure"></a>ASEGURARSE y ENSURE_VALID

Use para validar la exactitud de los datos.

### <a name="syntax"></a>Sintaxis

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión booleana que se va a probar.

### <a name="remarks"></a>Observaciones

El propósito de estas macros es mejorar la validación de los parámetros. Las macros impiden el procesamiento posterior de parámetros incorrectos en el código. A diferencia de las macros Assert, las macros de se ASEGURAn de producir una excepción además de generar una aserción.

Las macros se comportan de dos maneras, según la configuración del proyecto. Las macros llaman a Assert y, a continuación, inician una excepción si se produce un error en la aserción. Por lo tanto, en las configuraciones de depuración (es decir, donde se define _DEBUG), las macros generan una aserción y una excepción mientras se están en las configuraciones de versión, las macros solo producen la excepción (Assert no evalúa la expresión en configuraciones de versión).

La macro ENSURE_ARG actúa como la macro de Sure.

ENSURE_VALID llama a la macro ASSERT_VALID (que solo tiene efecto en las compilaciones de depuración). Además, ENSURE_VALID produce una excepción si el puntero es NULL. La prueba NULL se realiza en las configuraciones Debug y Release.

Si se produce un error en cualquiera de estas pruebas, se muestra un mensaje de alerta de la misma manera que la ASERCIÓN. Si es necesario, la macro produce una excepción de argumento no válido.
### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="this_file"></a>THIS_FILE

Se expande hasta el nombre del archivo que se está compilando.

### <a name="syntax"></a>Sintaxis

```
THIS_FILE
```

### <a name="remarks"></a>Observaciones

La información la usan las macros Assert y VERIFY. El Asistente para aplicaciones y los asistentes para código colocan la macro en los archivos de código fuente que crean.

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

##  <a name="trace"></a>  TRACE

Envía la cadena especificada al depurador de la aplicación actual.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Observaciones

Consulte [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) para obtener una descripción del seguimiento. TRACE y ATLTRACE2 tienen el mismo comportamiento.

En la versión de depuración de MFC, esta macro envía la cadena especificada al depurador de la aplicación actual. En una compilación de versión, esta macro se compila en nada (no se genera ningún código).

Para obtener más información, vea [depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="verify"></a>  VERIFY

En la versión de depuración de MFC, evalúa su argumento.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión (incluidos los valores de puntero) que se evalúa como un valor distinto de cero o 0.

### <a name="remarks"></a>Observaciones

Si el resultado es 0, la macro imprime un mensaje de diagnóstico y detiene el programa. Si la condición es distinto de cero, no hace nada.

El mensaje de diagnóstico tiene la forma

`assertion failed in file <name> in line <num>`

donde *Name* es el nombre del archivo de código fuente y *NUM* es el número de línea de la aserción que produjo un error en el archivo de código fuente.

En la versión de lanzamiento de MFC, VERIFY evalúa la expresión, pero no imprime ni interrumpe el programa. Por ejemplo, si la expresión es una llamada de función, se realizará la llamada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext en MFC)

Proporciona funcionalidad básica de volcado de objetos en la aplicación.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Observaciones

`afxDump` es un objeto [CDumpContext](../../mfc/reference/cdumpcontext-class.md) predefinido que permite enviar información de `CDumpContext` a la ventana de salida del depurador o a un terminal de depuración. Normalmente, se proporciona `afxDump` como un parámetro a `CObject::Dump`.

En Windows NT y en todas las versiones de Windows, `afxDump` salida se envía a la ventana de depuración de salida de Visual C++ al depurar la aplicación.

Esta variable solo se define en la versión de depuración de MFC. Para obtener más información sobre `afxDump`, vea [depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="afxdump"></a>AfxDump (interno)

Función interna que utiliza MFC para volcar el estado de un objeto durante la depuración.

### <a name="syntax"></a>Sintaxis

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Un puntero a un objeto de una clase derivada de `CObject`.

### <a name="remarks"></a>Observaciones

`AfxDump` llama a la función miembro de `Dump` de un objeto y envía la información a la ubicación especificada por la variable `afxDump`. `AfxDump` solo está disponible en la versión de depuración de MFC.

El código de programa no debe llamar a `AfxDump`, sino que debe llamar a la función miembro `Dump` del objeto adecuado.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxmemdf"></a>  afxMemDF

Esta variable es accesible desde un depurador o el programa y permite optimizar el diagnóstico de asignación.

```
int  afxMemDF;
```

### <a name="remarks"></a>Observaciones

`afxMemDF` puede tener los siguientes valores, tal y como se especifica en la enumeración `afxMemDF`:

- `allocMemDF` activa el asignador de depuración (valor predeterminado en la biblioteca de depuración).

- `delayFreeMemDF` retrasa la liberación de memoria. Mientras el programa libera un bloque de memoria, el asignador no devuelve esa memoria al sistema operativo subyacente. Esto hará que el programa tenga una carga de memoria máxima.

- `checkAlwaysMemDF` llama a `AfxCheckMemory` cada vez que se asigna o se libera memoria. Esto reducirá considerablemente las asignaciones de memoria y desasignaciones.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

Esta función prueba el SCODE pasado para ver si es un error.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Observaciones

Si es un error, la función produce una excepción. Si el SCODE pasado es E_OUTOFMEMORY, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) llamando a [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). De lo contrario, la función produce una [COleException](../../mfc/reference/coleexception-class.md) llamando a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Esta función se puede utilizar para comprobar los valores devueltos de las llamadas a funciones OLE en la aplicación. Al probar el valor devuelto con esta función en la aplicación, puede reaccionar correctamente a las condiciones de error con una cantidad mínima de código.

> [!NOTE]
>  Esta función tiene el mismo efecto en las compilaciones de depuración y que no son de depuración.

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

Distinto de cero si no hay errores de memoria; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si la función no detecta daños en la memoria, no imprime nada.

Se comprueban todos los bloques de memoria asignados actualmente en el montón, incluidos los asignados por **nuevas** pero no los asignados por llamadas directas a los asignadores de memoria subyacentes, como la función **malloc** o la función de Windows `GlobalAlloc`. Si se detecta que un bloque está dañado, se imprime un mensaje en la salida del depurador.

Si incluye la línea

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

en un módulo de programa, las llamadas posteriores a `AfxCheckMemory` muestran el nombre de archivo y el número de línea donde se asignó la memoria.

> [!NOTE]
>  Si el módulo contiene una o más implementaciones de clases serializables, debe colocar la línea de `#define` después de la última llamada a la macro IMPLEMENT_SERIAL.

Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxdump"></a>AfxDump (MFC)

Llame a esta función en el depurador para volcar el estado de un objeto durante la depuración.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Un puntero a un objeto de una clase derivada de `CObject`.

### <a name="remarks"></a>Observaciones

`AfxDump` llama a la función miembro de `Dump` de un objeto y envía la información a la ubicación especificada por la variable `afxDump`. `AfxDump` solo está disponible en la versión de depuración de MFC.

El código de programa no debe llamar a `AfxDump`, sino que debe llamar a la función miembro `Dump` del objeto adecuado.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxdumpstack"></a>  AfxDumpStack

Esta función global puede usarse para generar una imagen de la pila actual.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parámetros

*dwTarget*<br/>
Indica el destino de la salida del volcado. Los valores posibles, que se pueden combinar mediante el operador bit a **&#124;** bit or (), son los siguientes:

- AFX_STACK_DUMP_TARGET_TRACE envía la salida por medio de la macro [Trace](#trace) . La macro TRACE genera una salida solo en las compilaciones de depuración; no genera ninguna salida en las compilaciones de versión. Además, el seguimiento se puede redirigir a otros destinos además del depurador.

- AFX_STACK_DUMP_TARGET_DEFAULT envía la salida del volcado al destino predeterminado. En una compilación de depuración, la salida va a la macro TRACE. En una versión de lanzamiento, la salida se dirige al portapapeles.

- AFX_STACK_DUMP_TARGET_CLIPBOARD solo envía los resultados al portapapeles. Los datos se colocan en el portapapeles como texto sin formato mediante el CF_TEXT formato del portapapeles.

- AFX_STACK_DUMP_TARGET_BOTH envía la salida al portapapeles y a la macro TRACE, simultáneamente.

- AFX_STACK_DUMP_TARGET_ODS envía la salida directamente al depurador por medio de la función de Win32 `OutputDebugString()`. Esta opción generará la salida del depurador en las compilaciones de depuración y lanzamiento cuando se asocia un depurador al proceso. AFX_STACK_DUMP_TARGET_ODS siempre alcanza el depurador (si está asociado) y no se puede redirigir.

### <a name="remarks"></a>Observaciones

En el ejemplo siguiente se refleja una sola línea de la salida generada al llamar a `AfxDumpStack` desde un controlador de botón en una aplicación de cuadro de diálogo de MFC:

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

Cada línea de la salida anterior indica la dirección de la última llamada a función, el nombre de la ruta de acceso completa del módulo que contiene la llamada de función y el prototipo de función llamado. Si la llamada de función en la pila no se produce en la dirección exacta de la función, se muestra un desplazamiento de bytes.

Por ejemplo, en la tabla siguiente se describe la primera línea de la salida anterior:

|Output|Descripción|
|------------|-----------------|
|`00427D55:`|Dirección de devolución de la última llamada de función.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Nombre completo de la ruta de acceso del módulo que contiene la llamada de función.|
|`void AfxDumpStack(unsigned long)`|Prototipo de función llamado.|
|`+ 181 bytes`|Desplazamiento en bytes de la dirección del prototipo de función (en este caso, `void AfxDumpStack(unsigned long)`) a la dirección de devolución (en este caso, `00427D55`).|

`AfxDumpStack` está disponible en las versiones de depuración y de depuración de las bibliotecas MFC; sin embargo, la función siempre se vincula estáticamente, incluso cuando el archivo ejecutable utiliza MFC en un archivo DLL compartido. En implementaciones de bibliotecas compartidas, la función se encuentra en MFCS42. Biblioteca LIB (y sus variantes).

Para usar esta función correctamente:

- El archivo IMAGEHLP. DLL debe estar en su ruta de acceso. Si no tiene este archivo DLL, la función mostrará un mensaje de error. Vea la [biblioteca de ayuda de imágenes](/windows/win32/Debug/image-help-library) para obtener información sobre el conjunto de funciones proporcionado por IMAGEHLP.

- Los módulos que tienen marcos en la pila deben incluir información de depuración. Si no contienen información de depuración, la función seguirá generando un seguimiento de la pila, pero el seguimiento será menos detallado.
  ### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Habilita y deshabilita el volcado de pérdida de memoria en el destructor AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parámetros

*Archivos bdump*<br/>
de TRUE indica que el volcado de pérdida de memoria está habilitado; FALSE indica que el volcado de pérdida de memoria está deshabilitado.

### <a name="return-value"></a>Valor devuelto

Valor anterior de esta marca.

### <a name="remarks"></a>Observaciones

Cuando una aplicación descarga la biblioteca MFC, esta comprueba si hay pérdidas de memoria. En este momento, se envía una notificación a las pérdidas de memoria al usuario a través de la ventana **depuración** de Visual Studio.

Si la aplicación carga otra biblioteca antes que la biblioteca MFC, algunas asignaciones de memoria de la biblioteca se notificarán incorrectamente como pérdidas de memoria. Las pérdidas de memoria falsas pueden hacer que la aplicación se cierre lentamente, ya que la biblioteca MFC las estará notificando. En este caso, use `AfxEnableMemoryLeakDump` para deshabilitar el volcado de pérdida de memoria.

> [!NOTE]
>  Si usa este método para desactivar el volcado de pérdida de memoria, no recibirá ningún informe de pérdidas de memoria válidas en la aplicación. Solo debe usar este método si está seguro de que el informe de pérdida de memoria contiene pérdidas de memoria falsas.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

El seguimiento de la memoria de diagnóstico se habilita normalmente en la versión de depuración de MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parámetros

*bTrack*<br/>
Establecer este valor en TRUE activa el seguimiento de la memoria; FALSE lo desactiva.

### <a name="return-value"></a>Valor devuelto

La configuración anterior de la marca Track-enable.

### <a name="remarks"></a>Observaciones

Utilice esta función para deshabilitar el seguimiento de las secciones del código que sabe que asignan bloques correctamente.

Para obtener más información sobre `AfxEnableMemoryTracking`, vea [depurar aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

Comprueba una dirección de memoria para asegurarse de que representa un bloque de memoria actualmente activo asignado por la versión de diagnóstico de **nuevo**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Señala el bloque de memoria que se va a probar.

*nBytes*<br/>
Contiene la longitud del bloque de memoria en bytes.

*plRequestNumber*<br/>
Apunta a un entero **largo** que se rellenará con el número de secuencia de asignación del bloque de memoria, o bien, cero si no representa un bloque de memoria activo actualmente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el bloque de memoria está asignado actualmente y la longitud es correcta; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

También comprueba el tamaño especificado con respecto al tamaño asignado original. Si la función devuelve un valor distinto de cero, el número de secuencia de asignación se devuelve en *plRequestNumber*. Este número representa el orden en el que se asignó el bloque en relación con todas las demás asignaciones **nuevas** .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

Comprueba cualquier dirección de memoria para asegurarse de que está contenida completamente dentro del espacio de memoria del programa.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parámetros

*LP*<br/>
Apunta a la dirección de memoria que se va a probar.

*nBytes*<br/>
Contiene el número de bytes de memoria que se van a probar.

*bReadWrite*<br/>
Especifica si la memoria es para lectura y escritura (TRUE) o solo lectura (FALSE).

### <a name="return-value"></a>Valor devuelto

En compilaciones de depuración, distinto de cero si el bloque de memoria especificado está contenido completamente dentro del espacio de memoria del programa; de lo contrario, es 0.

En las compilaciones que no son de depuración, es distinto de cero si *LP* no es null; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La dirección no está restringida a los bloques asignados por **New**.

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

*lpsz*<br/>
Puntero que se va a probar.

*nLength*<br/>
Especifica la longitud de la cadena que se va a probar, en bytes. Un valor de-1 indica que la cadena terminará en NULL.

### <a name="return-value"></a>Valor devuelto

En compilaciones de depuración, distinto de cero si el puntero especificado apunta a una cadena con el tamaño especificado; de lo contrario, es 0.

En las compilaciones que no son de depuración, es distinto de cero si *lpsz* no es null; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

Establece un enlace que habilita la llamada de la función especificada antes de que se asigne cada bloque de memoria.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parámetros

*pfnAllocHook*<br/>
Especifica el nombre de la función a la que se va a llamar. Vea los comentarios para el prototipo de una función de asignación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si desea permitir la asignación; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El asignador de memoria de depuración biblioteca MFC puede llamar a una función de enlace definida por el usuario para permitir que el usuario supervise una asignación de memoria y controlar si se permite la asignación. Las funciones de enlace de asignación son prototipos como se indica a continuación:

**Bool AFXAPI AllocHook (size_t** `nSize` **, bool** `bObject` **, Long** `lRequestNumber` **);**

*nSize*<br/>
Tamaño de la asignación de memoria propuesta.

*bObject*<br/>
TRUE si la asignación es para un objeto derivado de `CObject`; en caso contrario, FALSE.

*lRequestNumber*<br/>
El número de secuencia de la asignación de memoria.

Tenga en cuenta que la Convención de llamada AFXAPI implica que el destinatario debe quitar los parámetros de la pila.

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

Llama a la función de iteración especificada para todas las clases derivadas de `CObject`serializable en el espacio de memoria de la aplicación.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Apunta a una función de iteración a la que se va a llamar para cada clase. Los argumentos de la función son un puntero a un objeto `CRuntimeClass` y un puntero void a datos adicionales que el llamador proporciona a la función.

*pContext*<br/>
Apunta a datos opcionales que el llamador puede proporcionar a la función de iteración. Este puntero puede ser NULL.

### <a name="remarks"></a>Observaciones

Las clases derivadas de `CObject`serializable son clases derivadas mediante la macro DECLARE_SERIAL. El puntero que se pasa a `AfxDoForAllClasses` en *pContext* se pasa a la función de iteración especificada cada vez que se llama.

> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

Ejecuta la función de iteración especificada para todos los objetos derivados de `CObject` que se han asignado con **New**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Apunta a una función de iteración que se va a ejecutar para cada objeto. Los argumentos de la función son un puntero a una `CObject` y un puntero void a datos adicionales que el llamador proporciona a la función.

*pContext*<br/>
Apunta a datos opcionales que el llamador puede proporcionar a la función de iteración. Este puntero puede ser NULL.

### <a name="remarks"></a>Observaciones

No se enumeran los objetos de pila, globales o incrustados. El puntero que se pasa a `AfxDoForAllObjects` en *pContext* se pasa a la función de iteración especificada cada vez que se llama.

> [!NOTE]
>  Esta función solo funciona en la versión de depuración de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CObject::D UMP](cobject-class.md#dump)
