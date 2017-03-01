---
title: Estructura CMemoryState | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure
- memory leaks, detecting
- detecting memory leaks
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
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
ms.openlocfilehash: 037c8f075a14346e3428c5e19bfda662c4f3c2b0
ms.lasthandoff: 02/24/2017

---
# <a name="cmemorystate-structure"></a>CMemoryState (estructura)
Proporciona una forma cómoda para detectar pérdidas de memoria en el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Crea una estructura de clase que controla los puntos de comprobación de memoria.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemoryState:: Checkpoint](#checkpoint)|Obtiene una instantánea (punto de comprobación) del estado de memoria actual.|  
|[CMemoryState:: Difference](#difference)|Calcula la diferencia entre dos objetos de tipo `CMemoryState`.|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Vuelca un resumen de todos los objetos actualmente asignados desde un punto de comprobación anterior.|  
|[CMemoryState:: DumpStatistics](#dumpstatistics)|Imprime las estadísticas de la asignación de memoria para un `CMemoryState` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CMemoryState`es una estructura y no tiene una clase base.  
  
 Una "pérdida de memoria" se produce cuando un objeto de memoria se asignan en el montón desasigna no cuando ya no sea necesario. Tales pérdidas de memoria con el tiempo pueden provocar errores de memoria insuficiente. Hay varias formas de asignar y desasignar memoria del programa:  
  
-   Mediante la `malloc` /  **libre** familia de funciones de la biblioteca de tiempo de ejecución.  
  
-   Mediante las funciones de administración de memoria de API de Windows, **LocalAlloc**/ **LocalFree** y **GlobalAlloc**/ **GlobalFree**.  
  
-   En C++ **nueva** y **eliminar** operadores.  
  
 El `CMemoryState` diagnóstico sólo ayuda a detectar memoria pérdidas producidas cuando asigna memoria mediante la **nueva** operador no se desasigna mediante **eliminar**. Son los dos grupos de funciones de administración de memoria para programas de C++ no y mezclarlos con **nueva** y **eliminar** en el mismo programa, no se recomienda. Una macro adicional, `DEBUG_NEW`, se proporciona para reemplazar la **nuevo** operador cuando necesite archivo y número de línea de seguimiento de asignaciones de memoria. `DEBUG_NEW`se utiliza siempre que se utilizaría normalmente la **nuevo** operador.  
  
 Al igual que con otros diagnósticos, el `CMemoryState` diagnóstico sólo está disponible en versiones de depuración del programa. Debe tener una versión de depuración del **_DEBUG** constante definida.  
  
 Si sospecha que el programa tiene una pérdida de memoria, puede utilizar el `Checkpoint`, **diferencia**, y `DumpStatistics` funciones para detectar la diferencia entre el estado de memoria (objetos asignados) en dos momentos diferentes en la ejecución del programa. Esta información puede ser útil para determinar si una función es limpiar todos los objetos que asigna.  
  
 Si simplemente saber dónde se produce el desequilibrio de la asignación y desasignación no proporciona suficiente información, puede utilizar el `DumpAllObjectsSince` función para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`. Este volcado de memoria muestra el orden de asignación, el archivo de origen y la línea que se ha asignado el objeto (si está utilizando `DEBUG_NEW` para la asignación) y la derivación del objeto, su dirección y su tamaño. `DumpAllObjectsSince`También llama a cada objeto `Dump` función para proporcionar información sobre su estado actual.  
  
 Para obtener más información acerca de cómo usar `CMemoryState` y otros diagnósticos, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Las declaraciones de objetos de tipo `CMemoryState` y llamadas a funciones miembro deben ir entre corchetes por `#if defined(_DEBUG)/#endif` directivas. Esto hace que se incluye sólo en versiones de depuración del programa de diagnóstico de memoria.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CMemoryState`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="a-namecheckpointa--cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState:: Checkpoint  
 Toma una instantánea de resumen de la memoria y lo almacena en este `CMemoryState` objeto.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Comentarios  
 El `CMemoryState` funciones miembro [diferencia](#difference) y [DumpAllObjectsSince](#dumpallobjectssince) utilizar estos datos de instantánea.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="a-namecmemorystatea--cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState  
 Construye una cadena vacía `CMemoryState` objeto que se debe rellenar por la [Checkpoint](#checkpoint) o [diferencia](#difference) función miembro.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities&#18;](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="a-namedifferencea--cmemorystatedifference"></a><a name="difference"></a>CMemoryState:: Difference  
 Compara dos `CMemoryState` objetos, a continuación, almacena la diferencia en este `CMemoryState` objeto.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Parámetros  
 *oldState*  
 El estado de memoria inicial definida por un `CMemoryState` punto de control.  
  
 *newState*  
 El nuevo estado de memoria definido por un `CMemoryState` punto de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los dos Estados de memoria son diferentes; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 [Punto de control](#checkpoint) debe llamar para cada uno de los dos parámetros de estado de la memoria.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="a-namedumpallobjectssincea--cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince  
 Llamadas el `Dump` función para todos los objetos de un tipo derivado de clase `CObject` que se asignaron (y todavía se asignan) desde la última [Checkpoint](#checkpoint) llamar para este `CMemoryState` objeto.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a `DumpAllObjectsSince` con una variable `CMemoryState` objeto volcará todos los objetos actualmente en memoria.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="a-namedumpstatisticsa--cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState:: DumpStatistics  
 Imprime un informe de estadísticas de memoria concisa de un `CMemoryState` objeto que se rellena mediante el [diferencia](#difference) función miembro.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Comentarios  
 El informe que se imprime en la [afxDump](http://msdn.microsoft.com/library/4b3cfa3f-fb75-456a-9d99-a5601acbcb11) dispositivo, se muestra lo siguiente:  
  
 Un informe de ejemplo proporciona información sobre el número o cantidad de:  
  
-   bloques libres  
  
-   bloques de tipo normal  
  
-   Bloques CRT  
  
-   Omitir bloques  
  
-   bloques cliente  
  
-   memoria máxima utilizada por el programa en cualquier momento (en bytes)  
  
-   memoria total utilizada actualmente por el programa (en bytes)  
  
 Los bloques libres son bloques cuya desasignación se retrasa si el número de `afxMemDF` se estableció en **delayFreeMemDF**. Para obtener más información, consulte [afxMemDF](diagnostic-services.md#afxmemdf), en la sección "MFC Macros y funciones globales". Consulte [tipos de bloques en el montón de depuración](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5) para obtener más información sobre estos tipos de bloques.  
  
### <a name="example"></a>Ejemplo  
  El siguiente código se debe colocar en *Nombre_proyecto*App.cpp. Definir las variables globales siguientes:  
  
 [!code-cpp[NVC_MFC_Utilities Nº&40;](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 En el `InitInstance` de función, agregue la línea:  
  
 [!code-cpp[NVC_MFC_Utilities nº&41;](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Agregar un controlador para el `ExitInstance` función y utilice el siguiente código:  
  
 [!code-cpp[NVC_MFC_Utilities&#42;](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Ahora puede ejecutar el programa en modo de depuración para ver el resultado de la `DumpStatistics` (función).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




