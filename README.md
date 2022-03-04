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

        CoroutineScope(Dispatchers.IO + completableJob!!).launch {

            val contacts = dispatcher.fetchContacts()

            withContext(Dispatchers.Main) {

                if (completableJob.complete()) {
                    //onComplete 
                }else{
                //show error
               }

            }

        }
