# Coroutine



        val  completableJob = Job()
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
