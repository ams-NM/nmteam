public:: true

- ## Events -Ongoing
	- {{query (and [[event]] (property :status "ongoing"))}}
	  query-table:: true
	  query-properties:: [:block :start]
	  query-sort-by:: start
	  query-sort-desc:: false
- ## 🗓️Schedule
	- {{query (and (task TODO DONE) (not [[Templates/monthly]]) (not [[Templates/misc]]))}}
	  query-table:: true
	  query-properties:: [:plan :block :finished :remark]
	  query-sort-by:: plan
	  query-sort-desc:: false
- ## Calibration Records
	- {{query (and [[cal-due]] (not [[Templates/misc]]))}}
	  query-table:: true
	  query-properties:: [:block :due :out :sn :wo]
- ## PR Pending
	- {{query (and [[pr-pending]] (not [[Templates/misc]]))}}
	  query-table:: true
	  query-properties:: [:block :pr :issued]
- ---
-
- ## Test query
  collapsed:: true
	- ```Clojure
	  {
	   :title [:b "Block query"]
	   :query [
	           :find (pull ?b [*])
	           :where
	           [?b :block/parent ?parent]
	           (not (has-property ?parent :template))
	           (task ?b #{"TODO", "DONE"})
	           (property ?b :plan "2023-04-05 Wed")
	           ]
	   }
	  ```
	- query-table:: true
	  #+BEGIN_QUERY
	  {
	   :title [:h2 "Block query"]
	   :query [
	           :find (pull ?b [*])
	           :where
	           [?b :block/parent ?parent]
	           (not (has-property ?parent :template))
	           (task ?b #{"TODO", "DONE"})
	           (property ?b :plan "2023-04-05 Wed")
	           ]
	   }
	  #+END_QUERY