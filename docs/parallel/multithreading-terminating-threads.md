---
title: 'Multithreading: finalizar subprocesos en MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 60c60d1aedf19ade6c84dafacd7de7a2e650e6ca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446271"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Multithreading: finalizar subprocesos en MFC

Dos situaciones normales hacen que un subproceso finalice: la función de control se cierra o no se permite que el subproceso se ejecute hasta su finalización. Si un procesador de textos usaba un subproceso para la impresión en segundo plano, la función controladora finalizaría normalmente si la impresión se completara correctamente. Sin embargo, si el usuario desea cancelar la impresión, el subproceso de impresión en segundo plano debe terminarse prematuramente. En este tema se explica cómo implementar cada situación y cómo obtener el código de salida de un subproceso una vez finalizada.

- [Terminación normal de subprocesos](#_core_normal_thread_termination)

- [Terminación prematura de subprocesos](#_core_premature_thread_termination)

- [Recuperar el código de salida de un subproceso](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="_core_normal_thread_termination"></a>Terminación normal de subprocesos

Para un subproceso de trabajo, la terminación normal de subprocesos es sencilla: salir de la función de control y devolver un valor que indica la razón de la finalización. Puede utilizar la función [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) o una instrucción **Return** . Normalmente, 0 significa finalización correcta, pero eso depende de usted.

Para un subproceso de la interfaz de usuario, el proceso es tan sencillo: desde dentro del subproceso de la interfaz de usuario, llame a [PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) en el Windows SDK. El único parámetro que toma `PostQuitMessage` es el código de salida del subproceso. Como en el caso de los subprocesos de trabajo, 0 normalmente significa que se ha completado correctamente.

## <a name="_core_premature_thread_termination"></a>Terminación prematura de subprocesos

Terminar un subproceso prematuramente es casi tan sencillo: llamar a [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) desde dentro del subproceso. Pase el código de salida deseado como único parámetro. Esto detiene la ejecución del subproceso, desasigna la pila del subproceso, desasocia todos los archivos dll asociados al subproceso y elimina el objeto de subproceso de la memoria.

se debe llamar a `AfxEndThread` desde dentro del subproceso para que se termine. Si desea terminar un subproceso desde otro subproceso, debe configurar un método de comunicación entre los dos subprocesos.

## <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Recuperar el código de salida de un subproceso

Para obtener el código de salida del subproceso de trabajo o de la interfaz de usuario, llame a la función [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) . Para obtener información sobre esta función, vea el Windows SDK. Esta función toma el identificador del subproceso (almacenado en el `m_hThread` miembro de datos de los objetos `CWinThread`) y la dirección de un valor DWORD.

Si el subproceso sigue activo, `GetExitCodeThread` coloca STILL_ACTIVE en la dirección DWORD proporcionada; de lo contrario, el código de salida se coloca en esta dirección.

Recuperar el código de salida de los objetos [CWinThread](../mfc/reference/cwinthread-class.md) supone un paso adicional. De forma predeterminada, cuando finaliza un subproceso de `CWinThread`, se elimina el objeto de subproceso. Esto significa que no puede tener acceso al miembro de datos `m_hThread` porque el objeto `CWinThread` ya no existe. Para evitar esta situación, realice una de las acciones siguientes:

- Establezca el miembro de datos `m_bAutoDelete` en FALSE. Esto permite que el objeto `CWinThread` sobreviva una vez finalizado el subproceso. Después, puede tener acceso al miembro de datos `m_hThread` una vez finalizado el subproceso. Sin embargo, si usa esta técnica, es el responsable de destruir el `CWinThread` objeto, ya que el marco no lo eliminará automáticamente. Este es el método preferido.

- Almacene el identificador del subproceso por separado. Una vez creado el subproceso, copie su `m_hThread` miembro de datos (mediante `::DuplicateHandle`) en otra variable y acceda a él a través de esa variable. De este modo, el objeto se elimina automáticamente cuando se produce la finalización y se puede averiguar por qué el subproceso ha terminado. Tenga cuidado de que el subproceso no finalice antes de que pueda duplicar el identificador. La manera más segura de hacerlo es pasar CREATE_SUSPENDED a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), almacenar el identificador y, a continuación, reanudar el subproceso llamando a [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Cualquier método le permite determinar por qué ha finalizado un objeto de `CWinThread`.

## <a name="see-also"></a>Consulte también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
