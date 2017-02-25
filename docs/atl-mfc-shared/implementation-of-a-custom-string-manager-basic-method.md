---
title: "Implementation of a Custom String Manager (Basic Method) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class, utilizar"
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementation of a Custom String Manager (Basic Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera más fácil de personalizar el esquema de asignación de memoria para los datos de la cadena es utilizar ATL\-proporcionó a la clase de **CAtlStringMgr** pero proporciona posee las rutinas de asignación de memoria.  El constructor de **CAtlStringMgr** toma un único parámetro: un puntero a un objeto de `IAtlMemMgr` .  `IAtlMemMgr` es una clase base abstracta que proporciona una interfaz genérica a una pila.  Mediante la interfaz de `IAtlMemMgr` , **CAtlStringMgr** asigna, reasigna, y libera la memoria usada para almacenar datos de cadena.  Puede o implementar la interfaz de `IAtlMemMgr` personalmente, o usar uno de los cinco ATL\-proporcionó a clases del administrador de memoria.  ATL\-proporcionó a las funciones existentes de asignación de memoria del ajuste de los administradores de memoria simplemente:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) Encapsula las funciones del montón de CRT estándar \([malloc](../c-runtime-library/reference/malloc.md), [libre](../c-runtime-library/reference/free.md), y [realloc](../c-runtime-library/reference/realloc.md)\)  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) Contiene un identificador de la pila de Win32, mediante [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), y [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) Encapsula las API Win32: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), y [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) Encapsula las API Win32: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), y [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) Ajusta el asignador API COM de tareas: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), y [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 Con el fin de administración de memoria de cadena, la clase más útil es `CWin32Heap` porque permite crear pilas independientes.  Por ejemplo, si desea utilizar un montón aparte solo para las cadenas, podría hacer lo siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Para utilizar este administrador privado de la cadena para administrar la memoria para una variable de `CString` , pase un puntero al administrador como parámetro al constructor de la variable de `CString` :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## Vea también  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)