# Coroutine



        val  completableJob = Job()


     completableJob.invokeOnCompletion {

            it?.message.let {
                var msg = it
                if (msg.isNullOrBlank()) {
                    msg = "Unknown cancellation error"
                    println("the ${completableJob} was cancelled : Reason ${msg}")
                }

            }

        }
    //  if (null!=completableJob && completableJob!!.isActive || completableJob!!.complete()) {
      //          completableJob!!.cancel(CancellationException("manually canceled , Reason: Undo"))
     // }
        CoroutineScope(Dispatchers.IO + completableJob!!).launch {

            val contacts = dispatcher.fetchContacts()
            delay(JOB_UNDO_TIME_OUT)
            withContext(Dispatchers.Main) {

                if (completableJob.complete()) {
                    //onComplete 
                }else{
                //show error
               }

            }

        }
