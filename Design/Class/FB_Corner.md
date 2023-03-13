# FB_Corner

```plantuml
@startuml
    interface ITF_ExecuteFB{
        # Prop_Execute
        BOOL : METH_Execute()
    }

    interface ITF_OutputFB{
        # Prop_Done
        # Prop_Busy
        # Prop_CommandAborted
        # Prop_Error
        # Prop_ErrorID
        BOOL : METH_Done()
        BOOL : METH_Busy()
        BOOL : METH_CommandAborted()
        BOOL : METH_Error()
    }

    interface ITF_ExtendsFB{
        BOOL : METH_Busy()
        BOOL : METH_Enter()
        BOOL : METH_Exit()
    }

    abstract FB_StatusExecuteFB{
        - bExecute
        - bDone
        - bBusy
        - bCommandAborted
        - bError
        - uiErrorID
        # Prop_Execute
        BOOL : METH_Execute()
        # Prop_Done
        # Prop_Busy
        # Prop_CommandAborted
        # Prop_Error
        # Prop_ErrorID
        BOOL : METH_Done()
        {Abstract} BOOL : METH_Busy()
        BOOL : METH_CommandAborted()
        BOOL : METH_Error()
        {Abstract} BOOL : METH_Enter()
        {Abstract} BOOL : METH_Exit()
    }

    class FB_MoveToPosition{
        + p_fbMover
        + Execute
        + Velocity
        + Acceleration
        + Deceleration
        + Jerk
        + Done
        + Busy
        + CommandAborted
        + Error
        + ErrorID
        BOOL : METH_Busy
        BOOL : METH_Enter
        BOOL : METH_Exit
    }
    class FB_Corner{
        + p_fbMover
        + Execute
        + Velocity
        + Acceleration
        + Deceleration
        + Jerk
        + Done
        + Busy
        + CommandAborted
        + Error
        + ErrorID
        BOOL : METH_Busy
        BOOL : METH_Enter
        BOOL : METH_Exit
    }

    FB_StatusExecuteFB ..|> ITF_OutputFB
    FB_StatusExecuteFB ..|> ITF_ExecuteFB
    FB_StatusExecuteFB ..|> ITF_ExtendsFB
    FB_Corner ..|> ITF_ExtendsFB
    FB_Corner --|> FB_StatusExecuteFB
    FB_Corner ..> FB_MoveToPosition
@enduml
```
