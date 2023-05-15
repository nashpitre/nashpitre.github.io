Permalink: timeline
Date: 11/15/2022
Page: yes
Menu: no

<style>
	* {
	  box-sizing: border-box;
	}
	body {
		color: {{text_color_dark}};
		background: #474e5d;
	}
	h1, h2, h3, h4, h5, h6 {
		color: {{link_color}};
	}
	strong, li, .kindle,
	 input[type="text"],
	  input[type="number"] {
		color: {{text_color_dark}};
	}
	.top_fill {
		background: black;
	}
	a {
	  border: none;
	}

	/* The actual timeline (the vertical ruler) */
	.timeline {
	  position: relative;
	  max-width: 1200px;
	  margin: 0 auto;
	  padding-top: 2rem;
	}

	/* The actual timeline (the vertical ruler) */
	.timeline::after {
	  content: '';
	  position: absolute;
	  width: 6px;
	  background-color: #F5F5F5;
	  top: 0;
	  bottom: 0;
	  left: 50%;
	  margin-left: -3px;
	}

	/* frame around content */
	.frame {
	  padding: 10px 40px;
	  position: relative;
	  background-color: inherit;
	  width: 50%;
	}

	/* The circles on the timeline */
	.frame::after {
	  content: '';
	  position: absolute;
	  width: 25px;
	  height: 25px;
	  right: -17px;
	  background-color: #F5F5F5;
	  border: 4px solid #FF9F55;
	  top: 15px;
	  border-radius: 50%;
	  z-index: 1;
	}

	/* Place the frame to the left */
	.left {
	  left: 0;
	}

	/* Place the frame to the right */
	.right {
	  left: 50%;
	}

	/* Add arrows to the left frame (pointing right) */
	.left::before {
	  content: " ";
	  height: 0;
	  position: absolute;
	  top: 22px;
	  width: 0;
	  z-index: 1;
	  right: 30px;
	  border: medium solid #F5F5F5;
	  border-width: 10px 0 10px 10px;
	  border-color: transparent transparent transparent #F5F5F5;
	}

	/* Add arrows to the right frame (pointing left) */
	.right::before {
	  content: " ";
	  height: 0;
	  position: absolute;
	  top: 22px;
	  width: 0;
	  z-index: 1;
	  left: 30px;
	  border: medium solid #F5F5F5;
	  border-width: 10px 10px 10px 0;
	  border-color: transparent #F5F5F5 transparent transparent;
	}

	/* Fix the circle for frames on the right side */
	.right::after {
	  left: -16px;
	}

	/* The actual content */
	.content {
	  padding: 20px 30px;
	  background-color: #F5F5F5;
	  position: relative;
	  border-radius: 6px;
	}
</style>

<div class="timeline">
	{{#all_entries}}
		{{#tagged.album}}
			<div class="frame right">
				<div class="content">
					<h2>{{title}}</h2>
					<p>{{body}}</p>
				</div>
			</div>
		{{/tagged.album}}
	{{/all_entries}}
</div>