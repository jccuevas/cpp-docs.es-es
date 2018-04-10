---
title: Estructura de CMemoryState | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20f4c2d7d33d07a5eca5a980c376056c3fe68e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmemorystate-structure"></a>Estructura de CMemoryState
Proporciona una manera cómoda para detectar pérdidas de memoria en el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Crea una estructura de tipo de clase que controla los puntos de comprobación de memoria.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryState:: Checkpoint](#checkpoint)|Obtiene una instantánea (punto de comprobación) del estado de memoria actual.|  
|[CMemoryState:: Difference](#difference)|Calcula la diferencia entre dos objetos de tipo `CMemoryState`.|  
|[CMemoryState:: DumpAllObjectsSince](#dumpallobjectssince)|Vuelca un resumen de todos los objetos asignados actualmente desde un punto de comprobación anterior.|  
|[CMemoryState:: DumpStatistics](#dumpstatistics)|Imprime las estadísticas de la asignación de memoria para un `CMemoryState` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CMemoryState`es una estructura y no tiene una clase base.  
  
 Una "pérdida de memoria" se produce cuando un objeto de memoria se asigna en el montón pero no cancela la asignación cuando ya no sea necesario. Finalmente, tales pérdidas de memoria pueden conducir a errores de memoria insuficiente. Hay varias formas de asignar y desasignar memoria en el programa:  
  
-   Mediante el `malloc` /  **libre** familia de funciones de la biblioteca de tiempo de ejecución.  
  
-   Mediante las funciones de administración de memoria de API de Windows, **LocalAlloc**/ **LocalFree** y **GlobalAlloc**/ **GlobalFree** .  
  
-   En C++ **nueva** y **eliminar** operadores.  
  
 El `CMemoryState` diagnóstico sólo ayuda a detectar memoria pérdidas producidas cuando asignó la memoria con el **nueva** operador no se desasigna mediante **eliminar**. Los otros dos grupos de funciones de administración de memoria son para los programas de C++ no y mezclar con **nueva** y **eliminar** no se recomienda en el mismo programa. Una macro adicional, `DEBUG_NEW`, se proporciona para reemplazar la **nueva** operador cuando necesite archivo y número de línea de seguimiento de las asignaciones de memoria. `DEBUG_NEW`se usa siempre que usaría normalmente la **nueva** operador.  
  
 Al igual que con otros diagnósticos, el `CMemoryState` diagnósticos solo están disponibles en versiones de depuración del programa. Debe tener una versión de depuración del **_DEBUG** constante definida.  
  
 Si sospecha que el programa tiene una fuga de memoria, puede usar el `Checkpoint`, **diferencia**, y `DumpStatistics` funciones para detectar la diferencia entre el estado de memoria (objetos asignados) en dos puntos distintos del programa ejecución. Esta información puede ser útil para determinar si una función es limpiar todos los objetos que asigna.  
  
 Si simplemente saber dónde se produce el desequilibrio en la asignación y desasignación no proporciona suficiente información, puede usar el `DumpAllObjectsSince` función para volcar todos los objetos asignados desde la llamada anterior a `Checkpoint`. Este volcado muestra el orden de asignación, el archivo de código fuente y la línea donde se ha asignado el objeto (si está utilizando `DEBUG_NEW` para la asignación) y la derivación del objeto, su dirección y su tamaño. `DumpAllObjectsSince`También llama a cada objeto `Dump` función para proporcionar información sobre su estado actual.  
  
 Para obtener más información sobre cómo usar `CMemoryState` y otros diagnósticos, vea [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Las declaraciones de objetos de tipo `CMemoryState` y llamadas a funciones miembro deben ser enmarcadas por `#if defined(_DEBUG)/#endif` directivas. Esto hace que se incluye sólo en versiones de depuración del programa de diagnóstico de memoria.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CMemoryState`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="checkpoint"></a>CMemoryState:: Checkpoint  
 Toma una instantánea resumen de memoria y lo almacena en esta `CMemoryState` objeto.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Comentarios  
 El `CMemoryState` funciones miembro [diferencia](#difference) y [DumpAllObjectsSince](#dumpallobjectssince) utilizar estos datos de instantánea.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="cmemorystate"></a>CMemoryState::CMemoryState  
 Construye un vacío `CMemoryState` objeto que se debe rellenar por la [punto de comprobación](#checkpoint) o [diferencia](#difference) función miembro.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>CMemoryState:: Difference  
 Compara dos `CMemoryState` objetos, a continuación, almacena la diferencia en esta `CMemoryState` objeto.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Parámetros  
 *oldState*  
 El estado de memoria inicial tal como se define por un `CMemoryState` punto de control.  
  
 *newState*  
 El nuevo estado de memoria según se define en un `CMemoryState` punto de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los dos Estados de memoria son diferentes; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 [Punto de comprobación](#checkpoint) debe llamar para cada uno de los dos parámetros de estado de la memoria.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="dumpallobjectssince"></a>CMemoryState:: DumpAllObjectsSince  
 Llamadas el `Dump` función para todos los objetos de un tipo derivado de la clase `CObject` que se asignaron (y todavía se asignan) desde la última [punto de comprobación](#checkpoint) llamar para este `CMemoryState` objeto.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a `DumpAllObjectsSince` con una sin inicializar `CMemoryState` objeto volcará todos los objetos actualmente en memoria.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CMemoryState](#cmemorystate) constructor.  
  
##  <a name="dumpstatistics"></a>CMemoryState:: DumpStatistics  
 Imprime un informe de estadísticas de memoria concisa desde una `CMemoryState` objeto que se rellena mediante la [diferencia](#difference) función miembro.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Comentarios  
 El informe, que se imprime en la [afxDump](diagnostic-services.md#afxdump) dispositivo, se muestra lo siguiente:  
  
 Un informe de ejemplo proporciona información sobre el número (o la cantidad) de:  
  
-   bloques libres  
  
-   bloques de tipo normal  
  
-   Bloques CRT  
  
-   Omitir bloques  
  
-   bloques cliente  
  
-   memoria máxima utilizada por el programa en cualquier momento (en bytes)  
  
-   memoria total utilizada actualmente por el sistema (en bytes)  
  
 Los bloques libres son el número de bloques cuya desasignación se retrasa si `afxMemDF` se estableció en **delayFreeMemDF**. Para obtener más información, consulte [afxMemDF](diagnostic-services.md#afxmemdf), en la sección "MFC Macros y funciones globales". Vea [tipos de bloques en el montón de depuración](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5) para obtener más información sobre estos tipos de bloques.  
  
### <a name="example"></a>Ejemplo  
  El siguiente código se debe colocar en *Nombre_proyecto*App.cpp. Defina las variables globales siguientes:  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 En el `InitInstance` funcionar, agregue la línea:  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Agregue un controlador para el `ExitInstance` función y utilice el código siguiente:  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Ahora puede ejecutar el programa en modo de depuración para ver el resultado de la `DumpStatistics` (función).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



