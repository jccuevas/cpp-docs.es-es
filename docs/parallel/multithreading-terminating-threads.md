---
title: 'Multithreading: Finalizar subprocesos en MFC | Microsoft Docs'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b192c0ee4bc7658fc39791545c4aa9334edd183
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131950"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading: Finalizar subprocesos en MFC
Hacer que un subproceso puede terminar dos situaciones normales: la función controladora finaliza o el subproceso no se puede ejecutar hasta su finalización. Si un procesador de textos, se usa un subproceso para impresión de fondo, la función controladora terminaría normalmente si la impresión se completa correctamente. Sin embargo, si el usuario desea cancelar la impresión, el subproceso de impresión en segundo plano tiene debe terminarse prematuramente. En este tema se explica cómo implementar cada situación y cómo obtener el código de salida de un subproceso después de que termine.  
  
- [Terminación normal de un subproceso](#_core_normal_thread_termination)  
  
- [Terminación prematura de subprocesos](#_core_premature_thread_termination)  
  
- [Recuperar el código de salida de un subproceso](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Terminación normal de un subproceso  
 
Para un subproceso de trabajo, la terminación normal es simple: salir de la función controladora y devolver un valor que indica la razón de finalización. Puede usar el [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) función o un **devolver** instrucción. Normalmente, 0 significa terminación sin error, pero que depende de usted.  
  
Para un subproceso de interfaz de usuario, el proceso es simple: desde el subproceso de interfaz de usuario, debe llamar a [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) en el SDK de Windows. El único parámetro que `PostQuitMessage` es el código de salida del subproceso. En cuanto a los subprocesos de trabajo, 0 suele significar terminación sin errores.  
  
##  <a name="_core_premature_thread_termination"></a> Terminación prematura de subprocesos  
 
Terminar un subproceso de forma prematura es casi igual de sencillo: llamar a [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) desde dentro del subproceso. Pasar el código de salida deseado como único parámetro. Esto detiene la ejecución del subproceso, cancela la asignación de la pila del subproceso, desconecte todas las DLL que se adjunta al subproceso y elimina el objeto de subproceso de la memoria.  
  
`AfxEndThread` Debe llamarse desde dentro del subproceso que se finalice. Si desea terminar el subproceso desde otro subproceso, debe configurar un método de comunicación entre los dos subprocesos.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Recuperar el código de salida de un subproceso  
 
Para obtener el código de salida de trabajo o el subproceso de interfaz de usuario, llame a la [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) función. Para obtener información acerca de esta función, consulte el SDK de Windows. Esta función recibe el identificador del subproceso (almacenado en el `m_hThread` miembro de datos de `CWinThread` objetos) y la dirección de un valor DWORD.  
  
Si el subproceso está aún activo, `GetExitCodeThread` coloca STILL_ACTIVE en la dirección DWORD suministrada; de lo contrario, el código de salida se coloca en esta dirección.  
  
Recuperar el código de salida [CWinThread](../mfc/reference/cwinthread-class.md) objetos requiere un paso adicional. De forma predeterminada, cuando un `CWinThread` subproceso finaliza, se elimina el objeto de subproceso. Esto significa que no se puede obtener acceso a la `m_hThread` miembro de datos porque el `CWinThread` objeto ya no existe. Para evitar esta situación, realice una de las siguientes acciones:  
  
- Establecer el `m_bAutoDelete` miembro de datos en FALSE. Esto permite la `CWinThread` objeto sobreviva después de que el subproceso ha terminado. A continuación, puede tener acceso a la `m_hThread` miembro de datos después de que el subproceso ha terminado. Si usa esta técnica, sin embargo, usted es responsable de destruir el `CWinThread` objeto porque el marco de trabajo no lo eliminará automáticamente. Este es el método preferido.  
  
- Store por separado el identificador del subproceso. Una vez creado el subproceso, copie su `m_hThread` miembro de datos (mediante `::DuplicateHandle`) a otra variable y tener acceso a él a través de esa variable. Esta forma, el objeto se elimina automáticamente cuando se produce la terminación y aún puede averiguar por qué terminó el subproceso. Tenga cuidado de que el subproceso no termina antes de poder duplicar el identificador. La forma más segura de hacerlo consiste en pasar CREATE_SUSPENDED a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), almacenar el identificador y, a continuación, reanudar el subproceso mediante una llamada a [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
Cualquiera de los métodos permite determinar por qué un `CWinThread` objeto finalizado.  
  
## <a name="see-also"></a>Vea también  
 
[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)   
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
[ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)